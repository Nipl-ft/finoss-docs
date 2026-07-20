# Technology Stack

| Field | Value |
|-------|-------|
| Project | fin.oss (Financial Operating System) |
| Document | 05_Technology_Stack.md |
| Version | 1.0.0 |
| Status | Draft |
| Repository | finoss-docs |
| Related Documents | 03_System_Architecture.md, 04_Project_Structure.md |

---

# Executive Summary

This document defines the official technology stack for **fin.oss**.

The selected technologies are based on the following goals:

- Reliability
- Performance
- Scalability
- Security
- Open-source ecosystem
- Beginner-friendly learning path
- Long-term maintainability

The architecture follows a modern client-server model with a React frontend, FastAPI backend, Supabase database, and Bybit exchange integration.

---

# Architecture Overview

```
┌───────────────────────────────┐
│         React Dashboard       │
│     React + Tailwind CSS      │
└──────────────┬────────────────┘
               │ HTTPS / REST API
┌──────────────▼────────────────┐
│         FastAPI Backend       │
│   Trading & Business Logic    │
└──────────────┬────────────────┘
               │
      ┌────────┴────────┐
      │                 │
┌─────▼───────┐  ┌──────▼────────┐
│ Supabase DB │  │ Bybit Exchange│
│ PostgreSQL  │  │ REST / WebSocket │
└─────────────┘  └───────────────┘
```

---

# Backend

## Python

### Purpose

Primary programming language for backend development.

### Why Python?

- Easy to learn
- Excellent financial libraries
- Strong AI ecosystem
- Large community
- Fast development

Version:

```
Python 3.12+
```

---

## FastAPI

### Purpose

Backend API framework.

### Responsibilities

- REST API
- Authentication
- Request validation
- Trading API
- Dashboard API
- Strategy API

### Benefits

- High performance
- Automatic API documentation
- Type checking
- Async support

---

# Frontend

## React

Purpose:

Build the web dashboard.

Responsibilities:

- Dashboard
- Charts
- Portfolio
- Settings
- Reports
- Authentication

---

## Tailwind CSS

Purpose:

Modern responsive UI.

Benefits:

- Fast styling
- Clean design
- Mobile-friendly
- Easy maintenance

---

## Vite

Purpose:

Frontend build tool.

Benefits:

- Fast startup
- Fast builds
- Hot reload

---

# Database

## Supabase

Purpose:

Backend-as-a-Service.

Provides:

- PostgreSQL database
- Authentication
- Row-Level Security (RLS)
- Realtime features
- Storage
- Edge Functions (future)

---

## PostgreSQL

Purpose:

Primary relational database.

Stores:

- Users
- Orders
- Positions
- Trades
- Market data
- Indicators
- Strategies
- Reports
- Logs

---

# Exchange Integration

## Bybit API

Purpose:

Trading and market data.

Used for:

- Authentication
- Account balance
- Orders
- Positions
- Market data
- WebSocket streams

Protocols:

- REST API
- WebSocket

---

# Technical Analysis

## pandas

Purpose:

Market data processing.

---

## NumPy

Purpose:

Numerical calculations.

---

## TA-Lib (or pandas-ta)

Purpose:

Technical indicators.

Examples:

- RSI
- EMA
- MACD
- ATR
- Bollinger Bands
- VWAP

---

# Data Visualization

## TradingView Lightweight Charts

Purpose:

Interactive price charts.

Displays:

- Candlesticks
- Indicators
- Trade markers

---

## Chart.js

Purpose:

Analytics charts.

Examples:

- Equity curve
- Portfolio allocation
- Performance metrics

---

# AI (Future Versions)

## PyTorch

Purpose:

Machine learning framework.

Future use:

- Strategy optimization
- Pattern recognition
- Model training

---

## Hugging Face Transformers

Purpose:

Natural language processing.

Future use:

- News analysis
- Market sentiment
- Report summarization

---

# Security

## JWT

Purpose:

Authentication tokens.

---

## bcrypt

Purpose:

Password hashing.

---

## python-dotenv

Purpose:

Load environment variables securely.

---

# Testing
