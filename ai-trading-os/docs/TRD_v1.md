TECHNICAL REQUIREMENTS DOCUMENT (TRD)

Project

AI Trading Operating System

Version: 1.0

Owner: AJ

Type: Personal Trading Intelligence Platform

---

1. SYSTEM ARCHITECTURE

Flutter Mobile App
        │
        ▼
FastAPI Backend
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Redis PostgreSQL WebSocket
        │
        ▼
Market Data Layer
        │
        ▼
Signal Engine
        │
        ▼
Chart Overlay Engine

---

2. TECHNOLOGY STACK

Frontend

- Flutter
- Riverpod
- Go Router
- Dio
- WebSocket

Backend

- FastAPI
- Uvicorn
- SQLAlchemy
- Alembic

Database

- PostgreSQL

Cache

- Redis

Realtime

- WebSocket

Deployment

- Docker

CI/CD

- GitHub Actions

Version Control

- Git

---

3. REPOSITORY STRUCTURE

ai-trading-os/

├── frontend/
│
├── backend/
│
├── docs/
│
├── scripts/
│
├── docker/
│
├── .github/
│
└── README.md

---

4. FRONTEND STRUCTURE

frontend/lib/

├── core/
│
├── models/
│
├── services/
│
├── providers/
│
├── screens/
│
├── widgets/
│
├── charts/
│
├── scanner/
│
├── options/
│
├── dashboard/
│
├── watchlist/
│
└── analytics/

---

5. BACKEND STRUCTURE

backend/

├── app/
│
├── api/
│
├── websocket/
│
├── scanners/
│
├── indicators/
│
├── strategies/
│
├── options/
│
├── alerts/
│
├── analytics/
│
├── database/
│
├── models/
│
├── schemas/
│
├── services/
│
└── utils/

---

6. DATABASE TABLES

users

id
username
created_at

watchlists

id
symbol
market
created_at

market_data

id
symbol
timestamp
open
high
low
close
volume
oi

signals

id
symbol
signal_type
entry
sl
target1
target2
target3
confidence
created_at
status

options_signals

id
symbol
strike
option_type
entry
sl
target1
target2
confidence

trades

id
symbol
entry
exit
pnl
strategy

alerts

id
message
created_at
status

---

7. REDIS CACHE

Store:

Live Price
Live OI
Live PCR
Scanner Output
Current Signals

Expiry:

1 Minute

---

8. WEBSOCKET FLOW

Market Feed
     │
     ▼
WebSocket Server
     │
     ▼
Redis
     │
     ▼
Flutter Client

Events

PRICE_UPDATE

SIGNAL_UPDATE

OPTION_UPDATE

ALERT_UPDATE

---

9. SCANNER ENGINE

Frequency

Every 5 Minutes

Scan Types

Breakout

Reversal

Momentum

Volume Spike

OI Build-up

Gap Up

Gap Down

Output

{
 "symbol":"RELIANCE",
 "score":94
}

---

10. INDICATOR ENGINE

Calculate

EMA20
EMA50
EMA200

RSI

MACD

ADX

ATR

VWAP

SuperTrend

Bollinger Bands

Store

Redis

---

11. MARKET REGIME ENGINE

Outputs

TRENDING_UP

TRENDING_DOWN

RANGE

VOLATILE

EVENT_DRIVEN

Logic

ADX
ATR
Volume
Structure

---

12. STRUCTURE ENGINE

Detect

Support

Resistance

Swing High

Swing Low

Breakout

Retest

Gap

Liquidity Zones

Store

structure_levels

---

13. MOMENTUM ENGINE

Inputs

RSI

MACD

ADX

Output

Momentum Score

0-100

---

14. VOLUME ENGINE

Analyze

Relative Volume

Volume Spike

Delivery Increase

Volume Breakout

Output

Volume Score

---

15. OPTIONS ENGINE

Inputs

OI

PCR

IV

Max Pain

Call Writing

Put Writing

Output

Bullish

Bearish

Neutral

---

16. SIGNAL ENGINE

Input Sources

Trend Score

Momentum Score

Volume Score

Options Score

Structure Score

Scoring

Trend       25

Momentum    20

Volume      20

Structure   20

Options     15

Total

100

Signal Rules

90+ Strong Buy

80+ Buy

70+ Watch

Below 70 Ignore

---

17. ENTRY CALCULATOR

Generate

Entry

SL

Target1

Target2

Target3

Based On

ATR

Support

Resistance

Risk Reward

---

18. OPTION STRIKE SELECTOR

Evaluate

ATM

ATM+1

ATM+2

ITM

OTM

Factors

Liquidity

OI

Volume

IV

Risk Reward

Output

Best Strike

---

19. CHART OVERLAY ENGINE

Draw

BUY Marker

SELL Marker

SL Line

Target Line

Support

Resistance

Color

Green Buy

Red Sell

---

20. ALERT ENGINE

Trigger

New Signal

Target Hit

SL Hit

High Confidence Setup

Delivery

App Push

Telegram Bot

---

21. TRADE TRACKER

Track

Entry

Current Price

PnL

Target Status

SL Status

States

ACTIVE

TARGET_HIT

SL_HIT

CLOSED

---

22. ANALYTICS ENGINE

Calculate

Win Rate

Loss Rate

Profit Factor

Drawdown

Average Reward

Average Risk

---

23. PERSONAL ANALYTICS

Track

Best Hour

Worst Hour

Best Strategy

Worst Strategy

Best Sector

Worst Sector

---

24. API ENDPOINTS

Authentication

POST /auth/login
POST /auth/register

Market

GET /market/live
GET /market/history

Scanner

GET /scanner/top

Signals

GET /signals
GET /signals/live

Options

GET /options/signals

Analytics

GET /analytics/performance

---

25. SECURITY

Use

JWT

HTTPS

Rate Limiting

---

26. GITHUB ACTIONS

Workflow

Push

↓

Test

↓

Build APK

↓

Create Release

↓

Upload APK

File

.github/workflows/android.yml

---

27. DOCKER

Services

backend

postgres

redis

Commands

docker compose up -d

---

28. MVP PHASE

Phase 1

Live Market

Scanner

Signal Engine

Chart Overlay

Phase 2

Options Engine

Telegram Alerts

Analytics

Phase 3

Personal AI Insights

Strategy Ranking

Weekly Reports

---

END OF TRD V1.0
