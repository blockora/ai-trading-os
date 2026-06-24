SIGNAL_ENGINE.md

Project: AI Trading Operating System

Version: 1.0

Purpose:

High-confidence BUY/SELL opportunities generate karna.

---

SIGNAL GENERATION FLOW

Market Data
    ↓
Market Regime
    ↓
Structure Analysis
    ↓
Trend Analysis
    ↓
Momentum Analysis
    ↓
Volume Analysis
    ↓
Options Analysis
    ↓
Score Calculation
    ↓
BUY / SELL / NO TRADE

---

SIGNAL TYPES

BUY

SELL

WATCHLIST

NO TRADE

---

MARKET REGIME FILTER

Before signal generation.

Allowed:

TRENDING_UP

TRENDING_DOWN

RANGE

Blocked:

EVENT_DRIVEN

EXTREME_VOLATILITY

Output:

PASS
FAIL

If FAIL

No Signal

---

TREND SCORE

Weight:

25 Points

Inputs:

EMA20

EMA50

EMA200

Rules

Strong Bullish

EMA20 > EMA50 > EMA200

Score:

25

Bullish

Score:

20

Neutral

Score:

10

Bearish

Score:

0

---

MOMENTUM SCORE

Weight:

20 Points

Inputs:

RSI

MACD

ADX

Scoring

RSI Bullish:

+5

MACD Bullish:

+5

ADX Strong:

+10

Maximum:

20

---

VOLUME SCORE

Weight:

20 Points

Inputs:

Volume Spike

Relative Volume

Delivery Increase

Scoring

Volume Spike:

+10

Relative Volume > 2x

+5

Delivery Increase

+5

Maximum

20

---

STRUCTURE SCORE

Weight:

20 Points

Inputs:

Support

Resistance

Breakout

Retest

Liquidity

Scoring

Breakout

+10

Successful Retest

+5

Liquidity Confirmation

+5

Maximum

20

---

OPTIONS SCORE

Weight:

15 Points

Inputs:

PCR

OI Change

Call Writing

Put Writing

Scoring

Bullish OI

+5

PCR Support

+5

Put Writing

+5

Maximum

15

---

TOTAL SCORE

Formula

Trend
+
Momentum
+
Volume
+
Structure
+
Options

Maximum

100

---

BUY RULES

Score >= 85

AND

Trend Score >= 20

AND

Volume Score >= 10

AND

Structure Score >= 10

Output

BUY

---

STRONG BUY

Score >= 90

AND

All Filters Confirmed

Output

STRONG BUY

---

SELL RULES

Score <= 20

OR

Bearish Confirmation

Output

SELL

---

WATCH RULES

Score

70 - 84

Output

WATCHLIST

No Marker

---

IGNORE RULES

Score

Below 70

Output

NO TRADE

---

CONFIDENCE CALCULATION

Formula

Score / 100

Examples

90 Score

90%

82 Score

82%

75 Score

75%

---

ENTRY CALCULATOR

Inputs

ATR

Support

Resistance

Current Price

Output

Entry

---

STOP LOSS CALCULATOR

Formula

Support - ATR

or

Resistance + ATR

Depending on trade direction.

---

TARGET CALCULATOR

Target 1

1:1

Target 2

1:2

Target 3

1:3

Risk Reward

---

CHART OVERLAY

BUY Marker

Green Arrow

SELL Marker

Red Arrow

Target Lines

Blue

Stop Loss

Orange

---

SIGNAL EXPIRY

Intraday

30 Minutes

Swing

1 Day

Options

15 Minutes

Expired Signals

Auto Archive

---

SIGNAL STATUS

NEW

ACTIVE

TARGET1_HIT

TARGET2_HIT

TARGET3_HIT

SL_HIT

EXPIRED

CLOSED

---

SIGNAL TRACKING

Store

Entry Time

Entry Price

Current Price

Status

PnL

---

PERFORMANCE TRACKING

For Every Signal

Store

Score

Outcome

PnL

Duration

Strategy

---

STRATEGY LEARNING

Calculate

Win Rate

Average Profit

Average Loss

Profit Factor

---

MINIMUM REQUIREMENTS

Signal Only If:

Score >= 85

Confidence >= 80

Market Regime PASS

Volume Confirmation PASS

Structure Confirmation PASS

Otherwise

NO SIGNAL

---

END OF SIGNAL_ENGINE V1.0
