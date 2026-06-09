# Intraday Scalping Playbook — NY AM Session

**Version 1.0 | Mechanical Execution System**

---

## Table of Contents

1. [Philosophy & Rules of Engagement](#1-philosophy--rules-of-engagement)
2. [Session Framework](#2-session-framework)
3. [Pre-Market Routine](#3-pre-market-routine)
4. [Market Bias Filter](#4-market-bias-filter)
5. [Core Setups](#5-core-setups)
6. [Entry Execution Rules](#6-entry-execution-rules)
7. [Stop Loss Rules](#7-stop-loss-rules)
8. [Take Profit Rules](#8-take-profit-rules)
9. [Trade Grading System (A+ / B / C)](#9-trade-grading-system-a--b--c)
10. [Overtrading Kill-Switch](#10-overtrading-kill-switch)
11. [No-Trade Conditions](#11-no-trade-conditions)
12. [Asia & London Session Rules](#12-asia--london-session-rules)
13. [Daily Checklist](#13-daily-checklist)
14. [Post-Session Review](#14-post-session-review)

---

## 1. Philosophy & Rules of Engagement

**Core Principle:** You are a sniper, not a machine gunner. Your edge comes from *waiting*, not from trading.

### Non-Negotiable Rules

1. **You do NOT need to trade every day.** A day with zero trades and zero losses is a *winning* day.
2. **You follow the playbook exactly.** No "I feel like it might work" trades.
3. **If the setup is not on this list, it does not exist.** Period.
4. **You accept 1:1 R:R.** You do not need home runs. You need consistency.
5. **You stop trading after your daily limit is hit.** No revenge trading, no "one more."

### Target Metrics

| Metric | Target |
|---|---|
| Win Rate | 58–65% |
| Risk:Reward | 1:1 minimum (1:1.5 optional extension) |
| Max Trades Per Session | 3 (NY AM) |
| Max Daily Trades | 4 total across all sessions |
| Max Consecutive Losses Before Stop | 2 |

---

## 2. Session Framework

### NY AM Session (PRIMARY) — 9:30 to 11:00 AM EST

This is your bread and butter. All three core setups are active.

| Time Window | Action |
|---|---|
| 9:15–9:30 | Final prep. Mark levels. Set alerts. Hands off the mouse. |
| 9:30–9:35 | **OBSERVE ONLY.** Do not trade. Let the opening candle print. |
| 9:35–9:45 | Opening Range forms (first 5-min or first 15-min candle). Mark OR high/low. |
| 9:45–10:30 | **Primary execution window.** All setups active. |
| 10:30–11:00 | Reduced activity. Only take A+ setups. Tighten criteria. |
| After 11:00 | **Session over.** Close charts or switch to review mode. |

### Key Rule: The First 5 Minutes

Do NOT place a trade in the first 5 minutes after the open. The 9:30–9:35 candle is for *reading*, not *reacting*. This single rule eliminates a large percentage of impulsive losers.

---

## 3. Pre-Market Routine (8:30–9:30 AM EST)

Complete this *every single day* before the bell. If you skip it, you do not trade.

### Step-by-Step

1. **Check the economic calendar.** Flag any red-folder events (FOMC, CPI, NFP, GDP). If a high-impact event falls within your session, see [No-Trade Conditions](#11-no-trade-conditions).

2. **Mark overnight highs and lows** on your chart (the range from 6:00 PM prior day to 9:30 AM).

3. **Mark previous day's high (PDH) and previous day's low (PDL).**

4. **Mark VWAP** (anchored to the current session open). It auto-plots at 9:30.

5. **Identify equal highs/lows or obvious liquidity pools** from the prior session and overnight. These are stop-hunt targets.

6. **Determine your bias** using the Bias Filter below.

7. **Set price alerts** at your key levels. Do NOT stare at the screen waiting. Let the market come to you.

8. **Write down your bias and top 2 levels** in your journal before the bell. This locks in your plan.

---

## 4. Market Bias Filter

You need a directional lean *before* the open. This is not a prediction — it is a framework for which side of the playbook to favor.

### Bias Determination (check in order)

| Step | Condition | Bias |
|---|---|---|
| 1 | Where is price relative to **yesterday's VWAP close**? Above = bullish lean. Below = bearish lean. | Directional lean |
| 2 | Where did the **overnight session settle** relative to the prior day's range? Upper third = bullish. Lower third = bearish. Middle third = neutral. | Confirmation or neutral |
| 3 | Is there a **clear equal high/low or liquidity pool** nearby that has not been swept? Expect price to reach for it before reversing. | Target identification |

### Bias Outcomes

- **Bullish Bias:** Favor longs. Only take shorts if a clear liquidity sweep + rejection occurs above a key level.
- **Bearish Bias:** Favor shorts. Only take longs if a clear liquidity sweep + rejection occurs below a key level.
- **Neutral/Conflicting Bias:** Only take A+ setups with the strongest confluence. Reduce max trades to 2.

---

## 5. Core Setups

You have exactly **three** setups. Nothing else.

---

### Setup 1: Opening Range Breakout (ORB)

**Timeframe:** 5-minute chart (use 1-min for entry precision)

**What it is:** The market establishes a range in the first 5–15 minutes. A breakout from this range, in the direction of your bias, is traded.

**Step-by-Step Entry Conditions:**

1. Wait for the first **5-minute candle** to close (9:35 AM). Mark its high and low — this is your Opening Range (OR).
   - *Optional:* Use the first 15 minutes (three 5-min candles) if the first candle is excessively wide (more than 1.5x the average 5-min range for that instrument). If the OR is too wide, skip it entirely.

2. Determine direction using your pre-market bias.
   - Bullish bias → Only trade the **breakout above** the OR high.
   - Bearish bias → Only trade the **breakdown below** the OR low.
   - Neutral bias → Skip the ORB entirely.

3. Wait for a **decisive candle close** above/below the OR level on the 5-min chart. A wick poking through does not count. The body must close beyond the level.

4. **Entry:** Enter on the *next candle's open* after the breakout candle closes, OR enter on a 1-minute pullback to the OR level (the level that was just broken should now act as support/resistance).

5. **Confirmation filter:** Volume on the breakout candle should be above the average of the first three 5-min candles. If volume is below average, downgrade the setup.

**Stop Loss:** Below the OR low (for longs) or above the OR high (for shorts). If the OR is too wide for your risk tolerance, use the midpoint of the OR as your stop — but only if the breakout candle closed strongly.

**Take Profit:** 1:1 measured from entry to stop. Optional 1.5:1 extension if price moves cleanly.

---

### Setup 2: VWAP Reclaim / Rejection

**Timeframe:** 5-minute chart (1-min for entry precision)

**What it is:** VWAP acts as a dynamic equilibrium. When price sweeps through VWAP and aggressively reclaims it, or when price tests VWAP from one side and rejects hard, there is a high-probability trade.

**Step-by-Step Entry Conditions:**

#### Variant A: VWAP Reclaim (mean reversion → trend continuation)

1. Price must be trading **below VWAP** (for a bullish reclaim) or **above VWAP** (for a bearish reclaim).

2. Price pushes through VWAP and **closes a 5-min candle on the other side** with a strong body (not a doji, not a spinning top).

3. The next 1–2 candles hold above/below VWAP (no immediate re-cross). This is the "acceptance" phase.

4. **Entry:** On the close of the acceptance candle, or on a 1-min pullback to VWAP that holds.

5. **Bias alignment:** The reclaim must be in the direction of your pre-market bias. A bullish reclaim against a bearish bias is a C-grade setup — skip it.

#### Variant B: VWAP Rejection (trend continuation)

1. Price is trending in one direction and pulls back to VWAP.

2. A **5-min candle touches or wicks into VWAP** but closes back in the direction of the trend (e.g., in a downtrend, price wicks up to VWAP but closes red below it).

3. The rejection candle must have a **visible wick** showing the rejection (long upper wick for bearish rejection, long lower wick for bullish rejection).

4. **Entry:** On the close of the rejection candle, or on the next candle's open.

5. **Bias alignment required.** VWAP rejections against your bias are not traded.

**Stop Loss:** For reclaims, stop goes on the opposite side of VWAP (the side price came from), placed at the wick low/high of the sweep candle. For rejections, stop goes beyond the VWAP wick by 1–2 ticks.

**Take Profit:** 1:1 minimum. If near PDH/PDL or another key level, consider taking profit early at 0.8R rather than holding into resistance.

---

### Setup 3: Liquidity Sweep + Rejection

**Timeframe:** 5-minute chart (1-min for entry precision)

**What it is:** The market hunts stops by sweeping past an obvious level (equal highs, equal lows, prior session high/low), then reverses. You trade the reversal.

**Step-by-Step Entry Conditions:**

1. **Identify the liquidity target** in your pre-market prep. This is an obvious level where stops are sitting:
   - Equal highs or equal lows (2+ touches at the same price)
   - Previous day high (PDH) or previous day low (PDL)
   - Overnight high (ONH) or overnight low (ONL)
   - Any clean horizontal level with multiple rejections

2. Price **sweeps the level** — it trades beyond it, taking out the stops. This shows as a wick or a quick spike through the level.

3. Price **immediately reverses back below/above the level** within 1–3 candles on the 5-min chart. The sweep candle closes back inside the prior range.

4. **Entry trigger:** On the 1-minute chart, wait for a candle that confirms the reversal:
   - For a bearish reversal (sweep of highs): A 1-min candle closes below the swept level with a bearish body.
   - For a bullish reversal (sweep of lows): A 1-min candle closes above the swept level with a bullish body.

5. **Entry:** On the close of that 1-min confirmation candle.

6. **Bias alignment:** Sweeps that reverse *into* your bias direction are A+ setups. Sweeps that reverse *against* your bias are B setups at best — take them only if the rejection is very clean and at a major level.

**Stop Loss:** Beyond the sweep wick high/low. This is the point where the thesis is invalidated — if price goes back through the sweep, the reversal failed.

**Take Profit:** 1:1 minimum. Natural extension target is the next key level or VWAP (if price is sweeping away from VWAP, the bounce back toward VWAP is the target).

---

## 6. Entry Execution Rules

These rules apply to ALL setups:

1. **Wait for candle close.** Never enter mid-candle on the 5-min chart. You may use 1-min candle closes for precision entries, but the 5-min setup candle must be closed first.

2. **No chasing.** If the entry candle moves more than 30% of your planned stop distance beyond your ideal entry before you enter, the trade is missed. Walk away. There will be another one.

3. **One attempt per setup.** If you enter a trade on a setup and get stopped out, you do NOT re-enter the same setup at the same level. The market told you the level failed. Listen.

4. **Pre-calculate your position size** before the session. Use a fixed dollar risk per trade (e.g., $50, $100 — whatever 1% of your account is). Calculate shares/contracts based on your stop distance. Do this math before the bell, not during live trading.

5. **Limit orders preferred.** For pullback entries, use limit orders at your predefined level. This removes the temptation to enter early.

---

## 7. Stop Loss Rules

| Rule | Detail |
|---|---|
| **Stop is placed at order entry** | Never enter a trade without a hard stop already set. No mental stops. |
| **Stop is based on structure** | It goes beyond the invalidation level for the setup (OR edge, VWAP wick, sweep wick). |
| **Never widen a stop** | If you are tempted to move your stop further away, it means the trade is failing. Let it hit. |
| **Move stop to breakeven** | Only after price has moved 0.7R in your favor AND structure supports it (e.g., a 5-min candle has closed beyond midpoint). |
| **Maximum stop size** | Define a maximum stop size in dollars/ticks for your instrument. If the setup requires a wider stop than your max, skip the trade. |

---

## 8. Take Profit Rules

### Primary Target: 1:1 (1R)

- Take 100% of your position off at 1R.
- This is the default. This is what builds your equity curve. This is what gets you to 60%+ win rate.

### Optional Extension: 1.5R (for A+ setups only)

- If the setup grades as A+ AND price moves to 1R cleanly (no stalling), you may hold 50% of your position to 1.5R.
- Move stop to breakeven on the remaining 50%.
- If price stalls at 1R, take everything off. Do not let a winner become a loser.

### Hard Rule

- **Never move your take profit further away.** Greed kills more accounts than bad entries.
- If price is near your TP and you are tempted to "let it run," take the profit. You can always re-enter on a new setup.

---

## 9. Trade Grading System (A+ / B / C)

Grade every potential trade BEFORE entry. Only A+ and B trades are taken. C trades are **never** taken.

### A+ Setup (Take immediately)

All of the following must be true:

- [x] Setup matches one of the three core setups exactly
- [x] Bias alignment (trade direction matches pre-market bias)
- [x] Key level confluence (setup occurs at PDH/PDL, VWAP, OR level, or a clear liquidity level)
- [x] Clean price action (strong candle bodies, clear rejection wicks, no choppy indecision)
- [x] Volume confirmation (above-average volume on the trigger candle)
- [x] Time window (occurs between 9:35–10:30 AM)

**Confluences present: 5–6 out of 6. Take the trade.**

### B Setup (Take selectively — max 1 per session)

- [x] Setup matches a core setup
- [x] Bias alignment OR key level confluence (has one but not both)
- [x] Acceptable price action (not perfect but not messy)
- [ ] May lack volume confirmation or be slightly outside the ideal time window

**Confluences present: 3–4 out of 6. Take only if no A+ has appeared and you have trades remaining.**

### C Setup (DO NOT TAKE)

- Setup is "close enough" but requires you to *rationalize* why it works
- Against your bias
- In a choppy, range-bound market
- During the first 5 minutes or after 11:00 AM
- You are entering because you are bored, not because the setup is there

**If you have to convince yourself, it is a C. Walk away.**

---

## 10. Overtrading Kill-Switch

This system exists because you identified overtrading as your biggest problem. These are **hard rules**, not guidelines.

### Daily Limits

| Condition | Action |
|---|---|
| 3 trades taken in NY AM | **Stop trading NY AM.** No exceptions. |
| 2 consecutive losses | **Stop trading for the rest of the session.** |
| 1 loss greater than 1.5R (slippage, widened stop, etc.) | **Stop trading for the day.** Review what went wrong. |
| 4 total trades across all sessions | **Done for the day.** |
| Weekly loss limit hit (define: e.g., 5% of account) | **No trading for the rest of the week.** |

### The "Urge to Trade" Protocol

When you feel the urge to force a trade:

1. **Stand up.** Leave the screen for 60 seconds.
2. **Ask:** "Is this trade on my playbook, or am I making it up?"
3. **Grade it.** If it is not clearly A+ or B, it is a C. Do not take it.
4. **Remind yourself:** "Missing a trade costs me $0. Forcing a bad trade costs me real money."
5. If you still feel the urge after this, **close your charts for 15 minutes.**

### The 10-Minute Rule

After any trade (win or loss), wait a minimum of **10 minutes** before taking the next trade. This prevents emotional re-entry and revenge trading. Set a timer. Use the 10 minutes to:
- Log the trade in your journal
- Reset mentally
- Re-check your bias and remaining trade count

---

## 11. No-Trade Conditions

If any of these conditions are true, you do not trade. Period.

### Market Conditions

- [ ] **FOMC day** (announcement day — stay flat from 30 min before to 30 min after)
- [ ] **First 5 minutes** after market open (9:30–9:35)
- [ ] **Major news in progress** (CPI, NFP, GDP releasing during your session)
- [ ] **Holiday-shortened session** (volume is unreliable)
- [ ] **Gap > 1%** on the index/instrument you trade (wait for the ORB to form; if the OR is excessively wide, skip the day)
- [ ] **VWAP is flat and price is chopping around it** with no directional move for 15+ minutes (this is a range — not your edge)
- [ ] **Spread is abnormally wide** (pre-market liquidity issue or news-related)

### Personal Conditions

- [ ] You did not complete the pre-market routine
- [ ] You are distracted (phone, people talking, multitasking)
- [ ] You are emotional (angry from yesterday's loss, euphoric from yesterday's win, anxious)
- [ ] You are tired, hungover, sick, or otherwise not mentally sharp
- [ ] You are trading to "make back" a loss
- [ ] You are trading because you feel you "should" be trading

**Any single checkmark = no trading.** This is non-negotiable.

---

## 12. Asia & London Session Rules

These sessions are **optional** and used only for high-quality setups. The frequency is much lower.

### Asia Session (7:00 PM – 2:00 AM EST)

- **Only trade:** Liquidity sweeps at clear daily levels (PDH, PDL, weekly highs/lows).
- **Do NOT trade:** ORBs (Asia range is too tight) or VWAP setups (low volume makes VWAP unreliable).
- **Max trades:** 1.
- **Grade requirement:** A+ only. No B setups.
- **Instruments:** Only trade instruments that are liquid during Asia (e.g., Nikkei, AUD pairs, gold). Do not trade US indices during Asia — the spreads are wide and volume is thin.

### London Session (3:00 AM – 5:00 AM EST, focus on London open)

- **Trade all three setups**, but with heightened criteria:
  - ORB: Use the first 15-min range (London's open is less volatile than NY unless news drops).
  - VWAP: Anchor to the London session open. Reclaims are stronger than rejections in London.
  - Liquidity sweeps: Asia session highs/lows are the primary targets.
- **Max trades:** 2.
- **Grade requirement:** A+ and strong B only.
- **Time focus:** 3:00–5:00 AM EST is the window. After 5:00 AM, step away and prepare for NY.

### Critical Rule for Off-Sessions

If you traded Asia or London, your NY AM max trade count drops by the number of trades already taken. Your daily cap of 4 is absolute.

---

## 13. Daily Checklist

Print this. Tape it next to your monitor.

### Before the Bell (8:30–9:30 AM)

- [ ] Economic calendar checked. No red-flag events during session.
- [ ] Overnight high/low marked.
- [ ] PDH and PDL marked.
- [ ] Equal highs/lows and liquidity pools identified.
- [ ] Bias determined and written down.
- [ ] Top 2 levels written down.
- [ ] Position size calculated.
- [ ] Alerts set at key levels.
- [ ] Mentally sharp and focused (personal no-trade check passed).

### During Session (9:30–11:00 AM)

- [ ] Did NOT trade in the first 5 minutes.
- [ ] Every entry matches a playbook setup.
- [ ] Every trade was graded BEFORE entry (A+ or B only).
- [ ] Every trade has a hard stop and predefined take profit.
- [ ] Respected the 10-minute rule between trades.
- [ ] Did not exceed 3 trades.

### After Session (11:00 AM+)

- [ ] All trades logged (entry, exit, grade, notes).
- [ ] Reviewed each trade: was it playbook-compliant?
- [ ] Identified any rule violations.
- [ ] Noted one thing done well and one thing to improve.

---

## 14. Post-Session Review

### Trade Journal Template

For every trade, log:

| Field | Entry |
|---|---|
| Date | |
| Session | NY AM / London / Asia |
| Setup | ORB / VWAP Reclaim / VWAP Rejection / Liquidity Sweep |
| Grade | A+ / B / C (if you took a C, flag it red) |
| Bias | Bullish / Bearish / Neutral |
| Direction | Long / Short |
| Entry Price | |
| Stop Loss | |
| Take Profit | |
| Result | Win / Loss / Breakeven |
| R Multiple | e.g., +1R, -1R, +0.5R |
| Notes | What went right? What went wrong? Was it playbook-compliant? |

### Weekly Review (Sunday)

1. Total trades taken: ___
2. Playbook-compliant trades: ___ / ___
3. A+ setups taken: ___
4. B setups taken: ___
5. C setups taken (violations): ___
6. Win rate: ___%
7. Total R gained/lost: ___
8. Biggest lesson this week: ___
9. One rule to reinforce next week: ___

### The Only Metric That Matters Early On

For the first 30 days, your primary metric is **not** P&L. It is **playbook compliance rate.** Track what percentage of your trades followed every rule. Aim for 90%+. The profits follow discipline, not the other way around.

---

## Quick Reference Card

*Tear this page out and keep it at your desk.*

```
SETUPS:       ORB | VWAP Reclaim/Rejection | Liquidity Sweep
GRADE:        A+ or B only. If C, walk away.
BIAS:         Determined pre-market. Written down. Not changed mid-session.
TIME:         9:35–10:30 prime | 10:30–11:00 A+ only | After 11:00 DONE
MAX TRADES:   3 per NY session | 4 per day
STOP:         Hard. Structural. Never widened.
TARGET:       1R default | 1.5R extension for A+ only
KILL SWITCH:  2 consecutive losses = session over
FIRST 5 MIN:  OBSERVE ONLY
10-MIN RULE:  Wait 10 min between trades. No exceptions.
```

---

*"The goal is not to make money every day. The goal is to follow the process every day. The money is a byproduct of discipline."*
