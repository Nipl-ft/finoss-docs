# System Architecture

| Field | Value |
|-------|-------|
| Project | fin.oss (Financial Operating System) |
| Document | 03_System_Architecture.md |
| Version | 1.0.0 |
| Status | Draft |
| Repository | finoss-docs |
| Related Documents | 01_Project_Vision.md, 02_System_Requirements.md |

---

# Executive Summary

This document defines the high-level architecture of **fin.oss**, a personal AI-assisted cryptocurrency trading platform.

The architecture is designed around modularity, reliability, security, scalability, and maintainability. Every major feature is implemented as an independent module with well-defined responsibilities.

The initial release (v1.0) focuses on rule-based automated trading, while AI is introduced as a decision-support component rather than an autonomous trader.

---

# Architecture Goals

The architecture aims to:

- Build a modular trading platform.
- Keep trading logic independent from AI.
- Support secure exchange integration.
- Enable reliable data collection.
- Provide comprehensive analytics.
- Support future multi-exchange expansion.
- Maintain high testability and maintainability.

---

# Design Principles

## Modularity
Each module has a single responsibility and communicates through defined interfaces.

## Separation of Concerns
Presentation, business logic, data storage, and external integrations remain independent.

## Security First
Protect API credentials, trading data, and user information.

## Reliability
Recover gracefully from failures and continue operating whenever possible.

## Scalability
Allow future support for additional exchanges, strategies, and AI modules.

## Testability
Every module should be independently testable.

---

# High-Level Architecture

```text
                    React Dashboard
                           │
                           ▼
                    FastAPI Backend
                           │
      ┌────────────────────┼────────────────────┐
      │                    │                    │
 Trading Engine     Analytics Engine      AI Advisor
      │                    │                    │
      └────────────────────┼────────────────────┘
                           │
                 Supabase PostgreSQL
                           │
      ┌────────────────────┼────────────────────┐
      │                    │                    │
   Bybit API         News/Sentiment       Market Data
```

---

# System Layers

## 1. Presentation Layer

Responsibilities:

- User Interface
- Dashboard
- Reports
- Charts
- Configuration
- Notifications

Technology:

- React
- Tailwind CSS

---

## 2. API Layer

Responsibilities:

- Authentication
- Request validation
- API endpoints
- Session management

Technology:

- FastAPI

---

## 3. Business Logic Layer

Responsibilities:

- Trading Engine
- Strategy Engine
- Risk Management
- Portfolio Management
- Paper Trading
- Backtesting

Technology:

- Python

---

## 4. AI & Analytics Layer

Responsibilities:

- Market analysis
- Performance analysis
- Strategy evaluation
- Parameter recommendations
- Future machine learning

Technology:

- Python
- PyTorch (future)

---

## 5. Data Layer

Responsibilities:

- Store market data
- Store trades
- Store indicators
- Store reports
- Store logs
- Store settings

Technology:

- Supabase PostgreSQL

---

## 6. External Services

Connected services:

- Bybit Exchange
- News APIs (future)
- Sentiment APIs (future)

---

# Core Modules

## Authentication Module

Functions:

- Login
- Session management
- User settings
- API key management

---

## Exchange Module

Functions:

- Market data
- Orders
- Positions
- Wallet balances
- Order history

---

## Data Collection Engine

Collects:

- Candlesticks
- Order book
- Trades
- Funding rates
- Open Interest
- Mark Price
- Index Price

---

## Market Analysis Engine

Analyzes:

- Technical indicators
- Volatility
- Trend
- Momentum
- Market regime

---

## Strategy Engine

Responsibilities:

- Strategy execution
- Signal generation
- Entry conditions
- Exit conditions

---

## Risk Management Engine

Responsibilities:

- Position sizing
- Stop Loss
- Take Profit
- Trailing Stop
- Drawdown protection
- Daily loss limits

---

## Order Execution Engine

Responsibilities:

- Submit orders
- Modify orders
- Cancel orders
- Monitor execution
- Retry failed requests

---

## Paper Trading Engine

Responsibilities:

- Virtual balance
- Simulated execution
- Performance tracking

---

## Backtesting Engine

Responsibilities:

- Historical replay
- Strategy evaluation
- Metrics generation

---

## Portfolio Engine

Responsibilities:

- Balance tracking
- Asset allocation
- Profit & Loss
- Performance metrics

---

## Reporting Engine

Generates:

- Daily reports
- Weekly reports
- Monthly reports
- Yearly reports
- Strategy reports

---

## Dashboard Module

Displays:

- Portfolio
- Open positions
- Charts
- Strategy status
- Market status
- Performance
- Risk metrics

---

# Data Flow

```text
Bybit
   │
   ▼
Data Collection
   │
   ▼
Database
   │
   ▼
Market Analysis
   │
   ▼
Strategy Engine
   │
   ▼
Risk Management
   │
   ▼
Order Execution
   │
   ▼
Database
   │
   ▼
Dashboard
```

---

# Database Interaction

All modules interact with Supabase through a defined data access layer.

Examples:

- Read market data
- Store trades
- Store indicators
- Store reports
- Store logs

Direct database access from the frontend is avoided for trading operations.

---

# API Communication

The frontend communicates only with the FastAPI backend.

The backend communicates with:

- Supabase
- Bybit
- Future external services

This separation protects API credentials and centralizes business logic.

---

# Security Architecture

Security measures include:

- Secure authentication
- Environment variables for secrets
- HTTPS
- API key encryption
- Database Row-Level Security (RLS)
- Audit logging

Withdrawal permissions should always be disabled on exchange API keys.

---

# AI Architecture

Version 1.0

AI responsibilities:

- Analyze historical performance
- Suggest parameter improvements
- Summarize trading results

AI does **not** execute trades directly.

Future versions may introduce adaptive strategy recommendations after sufficient validation.

---

# Deployment Architecture

```text
Browser
    │
React Dashboard
    │
FastAPI Backend
    │
Supabase Database
    │
Bybit Exchange
```

Future deployment options:

- Docker
- VPS
- Cloud platforms

---

# Error Handling

The system should:

- Retry transient API failures
- Log all exceptions
- Notify users of critical errors
- Prevent duplicate order execution

---

# Logging

Log categories:

- API requests
- API responses
- Orders
- Errors
- User actions
- System events

---

# Monitoring

The platform should monitor:

- API connectivity
- Database health
- Order execution
- Strategy performance
- System resources

---

# Scalability

The architecture supports future expansion by adding:

- New exchanges
- Additional strategies
- New indicators
- AI models
- Notification services

without major redesign.

---

# Future Architecture

Planned enhancements include:

- Multi-exchange trading
- Distributed processing
- AI optimization
- Mobile application
- Advanced analytics
- Cloud deployment

---

# Related Documents

- 01_Project_Vision.md
- 02_System_Requirements.md
- 04_Project_Structure.md
- 05_Technology_Stack.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0.0 | July 2026 | Initial system architecture document |

---

© 2026 fin.oss Project
