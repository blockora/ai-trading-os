DATABASE SCHEMA v1.0

Project: AI Trading Operating System

Database: PostgreSQL

Version: 1.0

---

TABLE: users

Purpose:

User profile information

Columns:

id UUID PRIMARY KEY

username VARCHAR(100)

email VARCHAR(255)

created_at TIMESTAMP

updated_at TIMESTAMP

---

TABLE: watchlists

Purpose:

User watchlist

Columns:

id UUID PRIMARY KEY

symbol VARCHAR(50)

market VARCHAR(50)

created_at TIMESTAMP

---

TABLE: market_data

Purpose:

Historical candles

Columns:

id BIGSERIAL PRIMARY KEY

symbol VARCHAR(50)

market VARCHAR(50)

timeframe VARCHAR(20)

timestamp TIMESTAMP

open NUMERIC

high NUMERIC

low NUMERIC

close NUMERIC

volume BIGINT

oi BIGINT

created_at TIMESTAMP

Indexes:

(symbol)

(timestamp)

(symbol, timeframe)

---

TABLE: live_quotes

Purpose:

Latest market snapshot

Columns:

symbol VARCHAR(50) PRIMARY KEY

market VARCHAR(50)

ltp NUMERIC

change_percent NUMERIC

volume BIGINT

oi BIGINT

updated_at TIMESTAMP

---

TABLE: indicators

Purpose:

Calculated indicators

Columns:

id BIGSERIAL PRIMARY KEY

symbol VARCHAR(50)

timeframe VARCHAR(20)

ema20 NUMERIC

ema50 NUMERIC

ema200 NUMERIC

rsi NUMERIC

macd NUMERIC

adx NUMERIC

atr NUMERIC

vwap NUMERIC

supertrend NUMERIC

updated_at TIMESTAMP

---

TABLE: structure_levels

Purpose:

Support and resistance

Columns:

id BIGSERIAL PRIMARY KEY

symbol VARCHAR(50)

timeframe VARCHAR(20)

support_1 NUMERIC

support_2 NUMERIC

resistance_1 NUMERIC

resistance_2 NUMERIC

swing_high NUMERIC

swing_low NUMERIC

updated_at TIMESTAMP

---

TABLE: scanner_results

Purpose:

Scanner output

Columns:

id BIGSERIAL PRIMARY KEY

symbol VARCHAR(50)

scanner_type VARCHAR(50)

score NUMERIC

reason TEXT

created_at TIMESTAMP

---

TABLE: signals

Purpose:

Stock signals

Columns:

id BIGSERIAL PRIMARY KEY

symbol VARCHAR(50)

signal_type VARCHAR(20)

entry NUMERIC

stop_loss NUMERIC

target1 NUMERIC

target2 NUMERIC

target3 NUMERIC

confidence NUMERIC

score NUMERIC

status VARCHAR(20)

created_at TIMESTAMP

closed_at TIMESTAMP

---

TABLE: option_chain

Purpose:

Option chain storage

Columns:

id BIGSERIAL PRIMARY KEY

symbol VARCHAR(50)

expiry DATE

strike NUMERIC

option_type VARCHAR(10)

ltp NUMERIC

volume BIGINT

oi BIGINT

oi_change BIGINT

iv NUMERIC

updated_at TIMESTAMP

---

TABLE: option_signals

Purpose:

Options recommendations

Columns:

id BIGSERIAL PRIMARY KEY

symbol VARCHAR(50)

expiry DATE

strike NUMERIC

option_type VARCHAR(10)

entry NUMERIC

stop_loss NUMERIC

target1 NUMERIC

target2 NUMERIC

confidence NUMERIC

status VARCHAR(20)

created_at TIMESTAMP

---

TABLE: market_regime

Purpose:

Market state

Columns:

id BIGSERIAL PRIMARY KEY

symbol VARCHAR(50)

regime VARCHAR(30)

confidence NUMERIC

updated_at TIMESTAMP

---

TABLE: alerts

Purpose:

Notifications

Columns:

id BIGSERIAL PRIMARY KEY

title TEXT

message TEXT

alert_type VARCHAR(50)

status VARCHAR(20)

created_at TIMESTAMP

---

TABLE: trades

Purpose:

Manual trade tracking

Columns:

id BIGSERIAL PRIMARY KEY

symbol VARCHAR(50)

trade_type VARCHAR(20)

entry_price NUMERIC

exit_price NUMERIC

quantity INTEGER

pnl NUMERIC

strategy VARCHAR(100)

created_at TIMESTAMP

closed_at TIMESTAMP

---

TABLE: performance_stats

Purpose:

Strategy statistics

Columns:

id BIGSERIAL PRIMARY KEY

strategy_name VARCHAR(100)

total_trades INTEGER

wins INTEGER

losses INTEGER

win_rate NUMERIC

profit_factor NUMERIC

avg_reward NUMERIC

avg_risk NUMERIC

updated_at TIMESTAMP

---

TABLE: personal_analytics

Purpose:

Personal insights

Columns:

id BIGSERIAL PRIMARY KEY

best_hour VARCHAR(50)

worst_hour VARCHAR(50)

best_strategy VARCHAR(100)

worst_strategy VARCHAR(100)

best_sector VARCHAR(100)

worst_sector VARCHAR(100)

updated_at TIMESTAMP

---

TABLE: weekly_reports

Purpose:

Weekly summaries

Columns:

id BIGSERIAL PRIMARY KEY

week_start DATE

week_end DATE

total_signals INTEGER

wins INTEGER

losses INTEGER

best_strategy VARCHAR(100)

worst_strategy VARCHAR(100)

report_json JSONB

created_at TIMESTAMP

---

DATABASE INDEXES

market_data

(symbol, timeframe, timestamp)

signals

(symbol, created_at)

option_chain

(symbol, expiry, strike)

scanner_results

(score)

alerts

(created_at)

---

DATABASE TARGETS

Market Data Retention:

5 Years

Signal Retention:

Unlimited

Performance History:

Unlimited

Expected Rows:

market_data > 100 Million+

Use partitioning in future versions.
