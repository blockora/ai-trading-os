REDIS_SCHEMA.md

Project: AI Trading Operating System

Version: 1.0

Purpose:

Ultra-fast real-time cache layer for market data, signals, scanners, options, alerts and dashboard.

Database:

Redis 7+

Role:

- Realtime Cache
- WebSocket Data Source
- Scanner Cache
- Signal Cache
- Alert Queue
- Session Store

---

REDIS ARCHITECTURE

Market Feed
    ↓
Redis
    ↓
Signal Engine
    ↓
WebSocket
    ↓
Flutter App

---

KEY NAMING STANDARD

Format

module:entity:value

Examples

market:quote:RELIANCE

market:quote:NIFTY

signal:stock:RELIANCE

signal:option:NIFTY

scanner:breakout

dashboard:top_signals

---

MARKET QUOTES

Key

market:quote:{symbol}

Example

market:quote:RELIANCE

Value

{
  "symbol":"RELIANCE",
  "ltp":2980.50,
  "change":1.2,
  "volume":500000,
  "oi":120000,
  "updated_at":"timestamp"
}

TTL

60 Seconds

---

LIVE CANDLES

Key

market:candle:{symbol}:{timeframe}

Example

market:candle:RELIANCE:5m

Value

{
 "open":100,
 "high":105,
 "low":99,
 "close":103,
 "volume":5000
}

TTL

300 Seconds

---

INDICATORS CACHE

Key

indicator:{symbol}:{timeframe}

Example

indicator:RELIANCE:15m

Value

{
 "ema20":100,
 "ema50":95,
 "rsi":65,
 "macd":2.4,
 "adx":30
}

TTL

300 Seconds

---

MARKET REGIME

Key

regime:{symbol}

Example

regime:NIFTY

Value

{
 "regime":"TRENDING_UP",
 "confidence":88
}

TTL

60 Seconds

---

STRUCTURE LEVELS

Key

structure:{symbol}:{timeframe}

Example

structure:RELIANCE:1h

Value

{
 "support1":2500,
 "support2":2450,
 "resistance1":2550,
 "resistance2":2600
}

TTL

600 Seconds

---

STOCK SIGNAL CACHE

Key

signal:stock:{symbol}

Example

signal:stock:RELIANCE

Value

{
 "signal":"BUY",
 "entry":2980,
 "sl":2960,
 "target1":3010,
 "target2":3040,
 "confidence":82
}

TTL

1800 Seconds

---

OPTION SIGNAL CACHE

Key

signal:option:{symbol}

Example

signal:option:NIFTY

Value

{
 "strike":"25100 CE",
 "entry":120,
 "sl":95,
 "target1":150,
 "target2":180,
 "confidence":84
}

TTL

900 Seconds

---

SCANNER CACHE

Breakout

scanner:breakout

Momentum

scanner:momentum

Reversal

scanner:reversal

Value

[
 {
  "symbol":"RELIANCE",
  "score":94
 }
]

TTL

300 Seconds

---

TOP OPPORTUNITIES

Key

dashboard:top_opportunities

Value

[
 {
  "symbol":"RELIANCE",
  "score":94
 }
]

TTL

60 Seconds

---

OPTION HEATMAP

Key

option:heatmap

TTL

60 Seconds

---

SECTOR HEATMAP

Key

sector:heatmap

Value

{
 "banking":"strong",
 "it":"weak"
}

TTL

60 Seconds

---

ALERT QUEUE

Key

alerts:queue

Type

Redis List

Example

{
 "type":"TARGET_HIT",
 "symbol":"RELIANCE"
}

---

TELEGRAM ALERT QUEUE

Key

telegram:queue

Type

Redis List

Purpose

Pending Telegram Messages

---

ACTIVE TRADES

Key

trade:active:{id}

Example

trade:active:1001

TTL

Until Closed

---

USER DASHBOARD CACHE

Key

dashboard:user:{user_id}

TTL

300 Seconds

---

PERFORMANCE CACHE

Key

performance:summary

Value

{
 "win_rate":68,
 "profit_factor":1.9
}

TTL

300 Seconds

---

WEBSOCKET CHANNELS

Price Updates

ws:price

Signal Updates

ws:signal

Option Updates

ws:option

Alerts

ws:alert

---

PUB SUB STRUCTURE

Publish

market:update

Subscribe

ws:price

---

RATE LIMIT CACHE

Key

ratelimit:{ip}

TTL

60 Seconds

Purpose

API Protection

---

SESSION CACHE

Key

session:{user_id}

TTL

24 Hours

---

CACHE PRIORITY

Highest

Market Quotes

Signals

Options Signals

Medium

Scanner Results

Heatmaps

Low

Analytics

Reports

---

MEMORY MANAGEMENT

Eviction Policy

allkeys-lru

Max Memory

2GB (MVP)

8GB (Production)

---

REDIS TARGET LATENCY

Read

< 5ms

Write

< 5ms

WebSocket Push

< 100ms

---

END OF REDIS_SCHEMA V1.0
