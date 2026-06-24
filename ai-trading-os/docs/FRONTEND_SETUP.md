FRONTEND_SETUP.md

Project: AI Trading Operating System

Version: 1.0

Purpose:

Flutter mobile application architecture define karna.

Application Type:

Mobile First

Platform:

Android

Future:

iOS

---

OVERVIEW

Frontend Responsibilities

- Dashboard Display
- Live Market View
- Trading Chart
- Buy/Sell Signals
- Options Recommendations
- Alerts
- Analytics
- Watchlist

---

TECH STACK

Framework

Flutter

Language

Dart

State Management

Riverpod

Routing

Go Router

Networking

Dio

Realtime

WebSocket

Storage

Hive

Charts

TradingView WebView

---

PROJECT STRUCTURE

frontend/

├── lib/
│
├── assets/
│
├── test/
│
├── android/
│
└── pubspec.yaml

---

LIB STRUCTURE

lib/

├── core/
├── models/
├── providers/
├── services/
├── routes/
├── screens/
├── widgets/
├── dashboard/
├── charts/
├── signals/
├── options/
├── watchlist/
├── analytics/
└── settings/

---

CORE

Folder

core/

Contains

constants.dart

theme.dart

config.dart

colors.dart

---

MODELS

Folder

models/

Files

market_quote.dart

signal.dart

option_signal.dart

alert.dart

trade.dart

Purpose

API Data Models

---

SERVICES

Folder

services/

Files

api_service.dart

websocket_service.dart

storage_service.dart

Purpose

API Communication

---

PROVIDERS

Folder

providers/

Files

market_provider.dart

signal_provider.dart

option_provider.dart

alert_provider.dart

Purpose

State Management

---

ROUTES

Folder

routes/

File

app_router.dart

Pages

Dashboard

Chart

Options

Watchlist

Analytics

Settings

---

MAIN NAVIGATION

Bottom Navigation

Tabs

Dashboard

Scanner

Chart

Options

Analytics

---

DASHBOARD SCREEN

File

dashboard_screen.dart

Widgets

Market Status

Top Opportunities

Active Signals

Heatmap

Alerts

---

SCANNER SCREEN

Purpose

Market Opportunities

Sections

Breakout

Momentum

Reversal

Volume Spike

OI Activity

---

CHART SCREEN

Purpose

Main Trading Screen

Components

TradingView Chart

Buy Marker

Sell Marker

Targets

Stop Loss

Support

Resistance

---

OVERLAY COMPONENTS

Widgets

buy_marker.dart

sell_marker.dart

target_line.dart

sl_line.dart

structure_zone.dart

---

SIGNAL PANEL

Display

Signal Type

Confidence

Entry

SL

Targets

---

OPTIONS SCREEN

Purpose

Option Recommendations

Widgets

Market Bias

Best CE

Best PE

Confidence

OI Summary

PCR Summary

---

OPTION CARD

Display

Strike

Entry

SL

Target1

Target2

Confidence

---

WATCHLIST SCREEN

Features

Add Symbol

Delete Symbol

Search Symbol

Favorites

---

ANALYTICS SCREEN

Display

Win Rate

Profit Factor

Best Strategy

Worst Strategy

Performance Chart

---

ALERT SCREEN

Display

New Signals

Target Hit

SL Hit

System Alerts

---

SETTINGS SCREEN

Options

Theme

Notifications

Telegram

Data Refresh

---

WEBSOCKET INTEGRATION

Endpoint

/ws

Events

PRICE_UPDATE

SIGNAL_UPDATE

OPTION_UPDATE

ALERT

---

LOCAL STORAGE

Hive Boxes

settings

watchlist

alerts

Purpose

Offline Support

---

API INTEGRATION

Base URL

/api/v1

Modules

Market

Scanner

Signals

Options

Analytics

Alerts

---

THEME

Mode

Dark

Primary

Trading Style UI

---

CHART LAYOUT

Top

Symbol

Price

Market Status

Center

Chart

Bottom

Signal Panel

Options Panel

---

PERFORMANCE TARGETS

App Startup

< 3 Seconds

Chart Load

< 2 Seconds

Signal Refresh

< 5 Seconds

WebSocket Update

< 1 Second

---

ERROR HANDLING

Display

Network Error

Server Error

No Data

---

SECURITY

Store

JWT Token

Use

Secure Storage

Never Store

API Secrets

---

MVP SCREENS

Dashboard

Scanner

Chart

Options

Analytics

Settings

---

FUTURE FEATURES

v2

Smart Money Concepts

Order Blocks

FVG

v3

Voice Assistant

AI Summary

v4

Multi Device Sync

---

FRONTEND BUILD

Debug

flutter run

APK

flutter build apk

Release

flutter build apk --release

---

MVP CHECKLIST

Dashboard

Scanner

Chart

Signals

Options

Analytics

Alerts

Settings

WebSocket

API Integration

---

END OF FRONTEND_SETUP V1.0
