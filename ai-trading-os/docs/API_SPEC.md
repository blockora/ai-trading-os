API SPECIFICATION (API_SPEC.md)

Project: AI Trading Operating System

Version: 1.0

Protocol: REST + WebSocket

Format: JSON

Base URL:

/api/v1

---

AUTHENTICATION

Authentication Method

JWT Bearer Token

Header

Authorization: Bearer <token>

---

HEALTH CHECK

GET

/api/v1/health

Response

{
  "status": "ok"
}

---

MARKET MODULE

Live Quote

GET

/api/v1/market/live/{symbol}

Example

/api/v1/market/live/RELIANCE

Response

{
  "symbol": "RELIANCE",
  "ltp": 2980.50,
  "change_percent": 1.45,
  "volume": 500000,
  "oi": 120000
}

---

Historical Candles

GET

/api/v1/market/history

Query Params

symbol
timeframe
from
to

Example

/api/v1/market/history?symbol=RELIANCE&timeframe=5m

Response

[
  {
    "timestamp":"2026-01-01T09:15:00",
    "open":100,
    "high":105,
    "low":99,
    "close":103,
    "volume":5000
  }
]

---

WATCHLIST MODULE

Get Watchlist

GET

/api/v1/watchlist

Response

[
  {
    "symbol":"RELIANCE"
  }
]

---

Add Symbol

POST

/api/v1/watchlist

Body

{
  "symbol":"RELIANCE",
  "market":"NSE"
}

---

Delete Symbol

DELETE

/api/v1/watchlist/{symbol}

---

SCANNER MODULE

Top Opportunities

GET

/api/v1/scanner/top

Response

[
 {
   "symbol":"RELIANCE",
   "score":94,
   "setup":"Breakout"
 }
]

---

Scanner By Type

GET

/api/v1/scanner/{type}

Examples

/api/v1/scanner/breakout

/api/v1/scanner/reversal

/api/v1/scanner/momentum

---

SIGNAL MODULE

Live Signals

GET

/api/v1/signals/live

Response

[
 {
   "symbol":"RELIANCE",
   "signal":"BUY",
   "entry":2980,
   "sl":2960,
   "target1":3010,
   "target2":3040,
   "confidence":82
 }
]

---

Signal Details

GET

/api/v1/signals/{id}

Response

{
 "id":1,
 "symbol":"RELIANCE",
 "signal":"BUY",
 "score":92,
 "confidence":82
}

---

OPTIONS MODULE

Option Chain

GET

/api/v1/options/chain

Query

symbol
expiry

Example

/api/v1/options/chain?symbol=NIFTY

---

Best Strike

GET

/api/v1/options/recommendation

Response

{
 "symbol":"NIFTY",
 "bias":"BULLISH",
 "strike":"25100 CE",
 "entry":120,
 "sl":95,
 "target1":150,
 "target2":180,
 "confidence":78
}

---

Options Signals

GET

/api/v1/options/signals

---

MARKET REGIME

GET

/api/v1/regime

Response

{
 "symbol":"NIFTY",
 "regime":"TRENDING_UP",
 "confidence":88
}

---

STRUCTURE LEVELS

GET

/api/v1/structure

Query

symbol
timeframe

Response

{
 "support1":25000,
 "support2":24800,
 "resistance1":25200,
 "resistance2":25400
}

---

HEATMAP MODULE

GET

/api/v1/heatmap

Response

[
 {
   "sector":"BANKING",
   "strength":"STRONG"
 }
]

---

ALERT MODULE

Alerts List

GET

/api/v1/alerts

---

Create Alert

POST

/api/v1/alerts

Body

{
 "symbol":"RELIANCE",
 "price":3000
}

---

TRADE TRACKER

Active Trades

GET

/api/v1/trades/active

---

Add Trade

POST

/api/v1/trades

Body

{
 "symbol":"RELIANCE",
 "entry":2980,
 "quantity":10
}

---

Close Trade

POST

/api/v1/trades/close

Body

{
 "trade_id":1,
 "exit":3050
}

---

ANALYTICS

GET

/api/v1/analytics/performance

Response

{
 "win_rate":68,
 "profit_factor":1.9
}

---

PERSONAL ANALYTICS

GET

/api/v1/analytics/personal

Response

{
 "best_hour":"10AM",
 "best_strategy":"Breakout"
}

---

WEEKLY REPORTS

GET

/api/v1/reports/weekly

Response

{
 "wins":20,
 "losses":8
}

---

WEBSOCKET SPEC

Endpoint

/ws

---

PRICE UPDATE EVENT

{
 "event":"PRICE_UPDATE",
 "symbol":"RELIANCE",
 "ltp":2980
}

---

SIGNAL UPDATE EVENT

{
 "event":"SIGNAL_UPDATE",
 "symbol":"RELIANCE",
 "signal":"BUY"
}

---

OPTION UPDATE EVENT

{
 "event":"OPTION_UPDATE",
 "symbol":"NIFTY",
 "strike":"25100 CE"
}

---

ALERT EVENT

{
 "event":"ALERT",
 "message":"Target 1 Hit"
}

---

ERROR FORMAT

{
 "success":false,
 "message":"Invalid Symbol"
}

---

SUCCESS FORMAT

{
 "success":true,
 "data":{}
}

END OF API_SPEC V1.0
