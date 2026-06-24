CHART_OVERLAY.md

Project: AI Trading Operating System

Version: 1.0

Purpose:

Trading chart par AI generated information visually display karna.

System ka objective:

- Buy Zone dikhana
- Sell Zone dikhana
- Entry dikhana
- Stop Loss dikhana
- Targets dikhana
- Support Resistance dikhana
- Option Recommendation dikhana

User ko manually analysis karne ki zarurat minimum ho.

---

OVERLAY ARCHITECTURE

Live Market Data
        ↓
Signal Engine
        ↓
Chart Overlay Engine
        ↓
TradingView Chart
        ↓
Flutter UI

---

OVERLAY LAYERS

Layer 1

Price Candles

Layer 2

Indicators

Layer 3

Structure

Layer 4

Signals

Layer 5

Options Overlay

Layer 6

Alerts

---

BUY MARKER

Condition

BUY Signal Generated

Display

Green Arrow

Example

🟢 BUY

Position

Signal Candle Low

Information

Entry

SL

Confidence

---

SELL MARKER

Condition

SELL Signal Generated

Display

Red Arrow

Example

🔴 SELL

Position

Signal Candle High

Information

Entry

SL

Confidence

---

ENTRY ZONE

Display

Green Rectangle

Purpose

Recommended Buy Area

Data

{
  "entry_start":2980,
  "entry_end":2990
}

---

STOP LOSS ZONE

Display

Red Horizontal Line

Label

SL

Example

SL = 2960

---

TARGET LINES

Display

Blue Horizontal Lines

Levels

Target 1

Target 2

Target 3

Example

T1 = 3010

T2 = 3040

T3 = 3070

---

SUPPORT ZONES

Display

Green Transparent Band

Levels

Support 1

Support 2

Purpose

Potential Reversal Area

---

RESISTANCE ZONES

Display

Red Transparent Band

Levels

Resistance 1

Resistance 2

Purpose

Potential Selling Area

---

LIQUIDITY ZONES

Display

Yellow Band

Types

Liquidity Above

Liquidity Below

Purpose

Stop Hunt Detection

---

BREAKOUT MARKER

Condition

Confirmed Breakout

Display

Blue Label

Text

BREAKOUT

---

RETEST MARKER

Condition

Successful Retest

Display

Purple Label

Text

RETEST

---

MARKET REGIME BADGE

Top Right Corner

Values

TRENDING UP

TRENDING DOWN

RANGE

VOLATILE

Display

Badge

---

CONFIDENCE BADGE

Top Right

Example

Confidence

84%

Ranges

90+

Strong

80-89

Good

70-79

Average

Below 70

Hidden

---

OPTIONS OVERLAY

Only For

NIFTY

BANKNIFTY

Stock Options

---

OPTION RECOMMENDATION PANEL

Display

Floating Card

Example

25100 CE

Entry: 120

SL: 95

T1: 150

T2: 180

Confidence: 84%

---

CE OVERLAY

Bullish Recommendation

Display

Green Option Card

Position

Top Left

---

PE OVERLAY

Bearish Recommendation

Display

Red Option Card

Position

Top Left

---

OPTION STRIKE ZONE

Display

Highlighted Price Level

Text

Recommended Strike

---

SIGNAL STATUS PANEL

States

NEW

ACTIVE

TARGET1_HIT

TARGET2_HIT

TARGET3_HIT

SL_HIT

EXPIRED

CLOSED

Display

Bottom Information Bar

---

ACTIVE TRADE PANEL

Display

Floating Widget

Information

Entry

Current Price

PnL

Risk Reward

Time In Trade

---

ALERT OVERLAY

Display

Temporary Popup

Events

New Buy

New Sell

Target Hit

SL Hit

---

HEATMAP SHORTCUT

Button

Display

Sector Heatmap

Markets

NSE

US

Crypto

---

MULTI TIMEFRAME PANEL

Display

Horizontal Status Bar

Values

Daily

4H

1H

15M

5M

Color

Bullish

Green

Bearish

Red

Neutral

Grey

---

OVERLAY REFRESH RATE

Price

1 Second

Signals

5 Seconds

Options

5 Seconds

Heatmap

60 Seconds

---

MOBILE OPTIMIZATION

Maximum Visible Layers

6

Hide Low Priority Layers

When Zoomed Out

---

PERFORMANCE TARGETS

Chart Load

< 2 Seconds

Overlay Load

< 500ms

Marker Render

< 100ms

---

OVERLAY PRIORITY

Highest

Price

Signals

SL

Targets

Medium

Structure

Options

Low

Heatmap

Analytics

---

FUTURE VERSIONS

v2

Smart Money Concepts

Order Blocks

Fair Value Gaps

v3

AI Voice Explanation

v4

Auto Replay Mode

---

END OF CHART_OVERLAY V1.0
