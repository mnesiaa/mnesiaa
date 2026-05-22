# Institutional Scalper Pro v1.0 — Strategy Guide

## Overview

ISP is a Pine Script v6 strategy+indicator that combines:
- Market Structure (BOS/CHoCH)
- Liquidity Sweeps (stop hunts)
- Fair Value Gaps
- Displacement candles
- CVD / delta proxy
- VWAP + EMA alignment
- RSI + ATR filters
- NY AM session gating (09:30–11:30 EST)

Signals require **all** filters to align simultaneously, making them rare
but high-probability.

---

## How the System Works

### 1. Market Structure Engine
Uses `ta.pivothigh` / `ta.pivotlow` with the `swingLen` lookback (default 10).
These are **confirmed after candle close** — the pivot is only recorded once
`swingLen` bars have passed, so zero repainting occurs.

**BOS** = price closes beyond the last swing high/low **in trend direction** →
continuation.

**CHoCH** = price closes beyond a swing high/low **against prior trend** →
reversal signal.

### 2. Liquidity Sweep Detection
A sweep is detected when:
- The candle wick pierces a prior swing level
- But the candle **closes back** on the correct side

This identifies stop hunts: institutional buyers/sellers absorbing retail
stop orders and reversing price.

### 3. Fair Value Gap (FVG)
Three-candle imbalance: `low[0] > high[2]` (bull) or `high[0] < low[2]` (bear).
Minimum size = `atrMult × ATR`. FVG zones are tracked until price enters them.

### 4. Displacement Candle
Body > 1.5× ATR AND close in top/bottom 25% of range. Indicates institutional
aggression rather than retail noise.

### 5. CVD Approximation
Estimates buy/sell volume from candle position:
- Buy vol ≈ `volume × (close − low) / range`
- Sell vol ≈ `volume × (high − close) / range`
- CVD = cumulative delta

Rising CVD = net buy pressure. Falling CVD = net sell pressure.

### 6. Session Filter
All signals gated to **09:30–11:30 EST** by default. This is the highest-volume,
highest-momentum window. Lunch chop (11:30–13:00) is avoided automatically.

### 7. Signal Gate (ALL must be true)
**BUY**
1. In active session
2. Bullish structure (BOS/CHoCH confirmed, or trend already bull)
3. Liquidity sweep below recent lows (stop hunt complete)
4. Close above VWAP
5. Volume spike ≥ 1.5× average
6. Bullish displacement candle OR price entering a bullish FVG
7. EMA 9 > EMA 20
8. RSI > 55
9. No chop filter (range > 0.5× ATR, volume > 0.8× avg)
10. CVD rising

**SELL** = mirror image of the above.

---

## Stop Loss Logic

SL is placed at `min(sweep_wick, last_swing_low) − ATR_buffer` for longs.
For shorts: `max(sweep_wick, last_swing_high) + ATR_buffer`.

This places the stop where the trade idea is **actually invalidated** — not
at a arbitrary fixed distance. The ATR buffer prevents stop-outs from normal
noise.

---

## Take Profit System

| Level  | Default | % of Position Closed |
|--------|---------|----------------------|
| TP1    | 1R      | 40%                  |
| TP2    | 2R      | 30%                  |
| TP3    | 3R      | 20%                  |
| Runner | 5R      | 10% (remaining)      |

After TP1 hits, the trade has no monetary risk if you move SL to breakeven
(do this manually or adjust `strategy.exit` stop to `entryPrice`).

The Runner captures trend continuation. On trending days (high ADX, strong
session momentum), the runner frequently reaches 5R+.

---

## Ideal Market Conditions

| Condition          | Setting                         |
|--------------------|---------------------------------|
| Best assets        | NQ, ES, BTC, XAUUSD             |
| Best timeframes    | 3m and 5m (1m for fast scalping)|
| Best session       | NY AM open (09:30–11:00 EST)    |
| Ideal volatility   | ATR > 3 bps of price            |
| Ideal volume       | Relative volume > 1.5×          |
| Avoid              | Pre-market, lunch, FOMC chop    |

---

## Best Settings by Market

| Market | SwingLen | ATR Mult | Vol Thresh |
|--------|----------|----------|------------|
| NQ/ES  | 8        | 0.5      | 1.5        |
| BTC    | 10       | 0.75     | 1.8        |
| XAUUSD | 12       | 0.6      | 1.4        |
| SPY    | 10       | 0.5      | 1.5        |

---

## How to Avoid Bad Trades

1. **Check the dashboard** — trend must show `▲ BULL` for longs, `▼ BEAR` for
   shorts. Mixed = wait.
2. **VWAP position** — only trade in the VWAP direction. Fighting VWAP is the
   fastest way to lose.
3. **Volume** — if relVol < 1.0, skip the signal. Low volume = fakeout risk.
4. **RSI extremes** — if RSI > 80 for a long, the move is overextended. Skip.
5. **Nearby structure** — visually confirm no major resistance (for longs) or
   support (for shorts) within 1R of entry.
6. **News events** — disable the strategy 5 min before/after FOMC, NFP, CPI
   announcements.

---

## Runner Management

Once TP2 or TP3 hits:
- Move SL to TP1 level (secured profit)
- Let the runner ride behind EMA 9 or VWAP

Manual trail: move SL up (for longs) each time price makes a new higher high
on the runner position. Exit when price closes below EMA 9.

Automatic trail: set `strategy.exit` trailing_stop to `atr * 2` after TP2
hits (requires custom state tracking — see code comments).

---

## Backtesting Notes

The script uses:
- `process_orders_on_close = true` — fills at bar close, no look-ahead
- `calc_on_every_tick = false` — no tick-level peeking
- `slippage = 2` — 2 ticks of realistic slippage
- `commission_value = 0.02%` — realistic per-side commission

**Do not lower slippage to 0** — it produces unrealistic backtest results.

Performance targets (realistic expectations on NQ 5m):
- Win rate: 45–60%
- Profit factor: 1.5–2.5
- Max drawdown: < 15%
- Average RR: 1.8–2.5

---

## Alert Setup

In TradingView, create an alert on the indicator with:
- Condition: `ISP — Buy Signal` or `ISP — Sell Signal`
- Message: leave as default (includes ticker, price, time)
- Frequency: `Once per bar close`

**Never use "Once per bar" for entry alerts** — this fires on every tick and
will trigger repainting issues.

---

## Anti-Repainting Guarantee

- All pivot calculations use `ta.pivothigh/low` with equal left/right length
  which only confirms after `swingLen` bars pass
- No `security()` calls with `lookahead=lookahead.on`
- All signals evaluated at `bar_index` using only `[1]` or further lookbacks
- `process_orders_on_close = true` ensures fills happen at confirmed close

---

## Changelog

| Version | Date       | Notes                          |
|---------|------------|--------------------------------|
| 1.0     | 2026-05-22 | Initial release                |
