# Institutional Scalper Pro v1.4 — Strategy Guide

## Overview

ISP is a Pine Script v6 strategy+indicator that combines:
- Market Structure (BOS/CHoCH) via zero-lag rolling highs/lows
- Liquidity Sweeps (stop hunts)
- Fair Value Gaps
- Displacement candles
- CVD / delta proxy
- VWAP + EMA alignment
- RSI + ATR filters
- NY AM session gating (09:30–11:30 EST)
- Progressive stop management (breakeven → ATR trail)

Signals require **all** filters to align simultaneously, making them rare
but high-probability.

---

## How the System Works

### 1. Market Structure Engine

Uses `ta.highest` / `ta.lowest` over two lookback windows:
- **Near** (default 15 bars) — recent swing targets for sweep detection
- **Far** (default 40 bars) — macro structure for BOS/CHoCH

Both use `[1]` offset (already-closed bars) so signals are
**non-repainting** — they fire on the closing bar, never update after.

**BOS** = close crosses the far window high/low **in the prior trend direction** →
continuation.

**CHoCH** = close crosses the far window high/low **against prior trend** →
potential reversal.

### 2. Liquidity Sweep Detection

A sweep fires on the same candle it happens:
- Wick pierces `nearLow` (bull sweep) or `nearHigh` (bear sweep)
- Candle **closes back** on the correct side

The last sweep wick price is stored and used as the SL anchor.
A sweep is "recent" for `sweepWin` bars (default 3).

### 3. Fair Value Gap (FVG)

Three-candle imbalance: `low[0] > high[2]` (bull) or `high[0] < low[2]` (bear).
Minimum size = `fvgMinATR × ATR`. An FVG expires if price closes through it.
A gap counts as "recent" for `fvgWin` bars (default 4).

### 4. Displacement Candle

Body > 1.3× ATR AND close in top 70%+ of range (bull) / bottom 30%- (bear).
Indicates institutional aggression rather than retail noise. Fires in-bar,
no pivot wait required.

### 5. CVD Approximation

Estimates buy/sell volume from candle position:
- Buy vol ≈ `volume × (close − low) / range`
- Sell vol ≈ `volume × (high − close) / range`
- CVD = cumulative delta (resets on session open by convention)

Rising CVD = net buy pressure over the session. Falling = net sell.

### 6. Session Filter

All signals gated to **09:30–11:30 EST** by default (integer HHMM comparison,
works on all market data feeds). The session high/low are tracked from open.

### 7. Signal Gate (ALL must be true)

**BUY**
1. In active session
2. Recent bull liquidity sweep (≤ `sweepWin` bars ago)
3. Trend direction ≥ 0 OR EMA 9 > EMA 20
4. EMA 9 > EMA 20
5. Close above VWAP
6. Recent bull displacement OR price inside/near a bull FVG
7. Volume spike ≥ threshold OR rel-vol > 1.0
8. RSI > `rsiBullMin` (default 45) and rising
9. Delta positive OR CVD rising
10. Range > 0.35× ATR and volume > 0.75× average (chop filter)
11. No open position

**SELL** = mirror image of the above.

---

## Stop Loss Logic

SL is placed at `min(lastBullSweepLow, nearLow) − ATR_buffer` for longs.  
For shorts: `max(lastBearSweepHigh, nearHigh) + ATR_buffer`.

This places the stop where the trade idea is **actually invalidated** — not
at an arbitrary fixed distance. The ATR buffer (default 0.5× ATR) prevents
stop-outs from normal noise.

---

## Progressive Stop Management (v1.4)

The SL is not static — it advances automatically as the trade profits.

| Milestone | Trigger | SL Action |
|-----------|---------|-----------|
| TP1 tagged | `high >= lTP1` (long) | SL moves to entry price (breakeven) |
| TP2 tagged | `high >= lTP2` (long) | SL trails at `close − 2×ATR` |

For shorts the mirror conditions apply (`low <=` for TP tags).

The trailing stop only moves in the favorable direction (`math.max` for longs,
`math.min` for shorts), so it never widens. The dashboard shows **Breakevn**
and **Trail** status for the active position.

---

## Take Profit System

| Level  | Default | % of Position Closed |
|--------|---------|----------------------|
| TP1    | 1R      | 40%                  |
| TP2    | 2R      | 30%                  |
| TP3    | 3R      | 20%                  |
| Runner | 5R      | 10% (remaining)      |

R = `entry_price − longSL` (risk per unit). TP prices are calculated at
signal bar and held in `var float` so they persist through the trade.

After TP1, the strategy is at breakeven risk (automatic via progressive SL).  
The runner at 5R captures trend continuation with the ATR trail as a backstop.

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

| Market | NearLen | ATR Mult | Vol Thresh |
|--------|---------|----------|------------|
| NQ/ES  | 12      | 0.5      | 1.2        |
| BTC    | 15      | 0.75     | 1.5        |
| XAUUSD | 15      | 0.6      | 1.4        |
| SPY    | 12      | 0.5      | 1.2        |

---

## How to Avoid Bad Trades

1. **Check the dashboard** — trend must show `BULL` for longs, `BEAR` for
   shorts. `NEUT` = wait for a BOS/CHoCH to establish direction.
2. **VWAP position** — only trade in the VWAP direction. `BELOW VWAP` + long = skip.
3. **Volume** — if relVol < 1.0, the signal fires but the move will likely fizzle.
4. **RSI extremes** — if RSI > 80 on a long signal, the move is overextended. Skip.
5. **Nearby structure** — visually confirm no major resistance (longs) or
   support (shorts) within 1R of entry.
6. **News events** — disable 5 min before/after FOMC, NFP, CPI prints.

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
- Condition: `ISP Buy Signal` or `ISP Sell Signal`
- Message: leave as default (includes ticker, price, time)
- Frequency: `Once per bar close`

**Never use "Once per bar"** — this fires on every tick and introduces
look-ahead bias in the alerts.

---

## Anti-Repainting Guarantee

- Structure uses `ta.highest / ta.lowest` with `[1]` offset — only
  confirmed closed bars used, zero repainting
- No `security()` calls with `lookahead=lookahead.on`
- All signals evaluated using `[1]` or further lookbacks only
- `process_orders_on_close = true` ensures fills happen at confirmed close

---

## Changelog

| Version | Date       | Notes                                                      |
|---------|------------|------------------------------------------------------------|
| 1.0     | 2026-05-22 | Initial release                                            |
| 1.1     | 2026-05-22 | Two-phase sweep+confirmation architecture                  |
| 1.2     | 2026-05-22 | Labeled SL/TP lines on every signal                        |
| 1.3     | 2026-05-22 | Replace pivot-wait structure with zero-lag rolling highs   |
| 1.4     | 2026-05-24 | Progressive SL: breakeven after TP1, ATR trail after TP2  |
