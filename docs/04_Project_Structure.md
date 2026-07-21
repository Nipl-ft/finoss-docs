# Project Structure

| Field | Value |
|-------|-------|
| Project | fin.oss (Financial Operating System) |
| Document | 04_Project_Structure.md |
| Version | 1.0.0 |
| Status | Draft |
| Repository | finoss-docs |
| Related Documents | 01_Project_Vision.md, 03_System_Architecture.md |

---

# Executive Summary

This document defines the directory structure, repository organization, module layout, naming conventions, and development standards for the **fin.oss** project.

The objective is to create a clean, scalable, and maintainable project structure that supports long-term development and future enhancements.

---

# Project Organization

The project is organized into three repositories.

```
GitHub
│
├── finoss-docs      # Documentation
├── finoss           # Application Source Code
└── finoss-ai        # AI Research & Models (Future)
```

Each repository has a specific purpose and should evolve independently.

---

# Repository Responsibilities

## finoss-docs

Purpose:

- Project documentation
- Architecture
- Database design
- API documentation
- Roadmaps
- Development guides
- Diagrams

---

## finoss

Purpose:

- Backend services
- Frontend application
- Trading engine
- Risk management
- Dashboard
- Database migrations
- Tests

---

## finoss-ai (Future)

Purpose:

- AI experiments
- Model training
- Research notebooks
- Strategy optimization
- Machine learning pipelines

---

# finoss Directory Structure

```
finoss/
│
├── apps/
│   ├── backend/
│   └── frontend/
│
├── packages/
│   ├── common/
│   ├── indicators/
│   ├── trading-engine/
│   ├── risk-engine/
│   ├── analytics/
│   ├── portfolio/
│   ├── reporting/
│   ├── paper-trading/
│   ├── backtesting/
│   ├── exchange/
│   ├── notifications/
│   └── ai/
│
├── database/
│   ├── migrations/
│   ├── seeds/
│   └── schema/
│
├── infrastructure/
│   ├── docker/
│   ├── nginx/
│   └── deployment/
│
├── scripts/
│
├── tests/
│   ├── unit/
│   ├── integration/
│   ├── paper/
│   └── backtesting/
│
├── docs/
│
├── assets/
│
├── .github/
│   └── workflows/
│
├── .env.example
├── README.md
├── pyproject.toml
├── requirements.txt
└── docker-compose.yml
```

---

# Backend Structure

```
backend/
│
├── api/
├── auth/
├── config/
├── core/
├── database/
├── middleware/
├── models/
├── routers/
├── services/
├── utils/
└── main.py
```

---

# Frontend Structure

```
frontend/
│
├── public/
│
├── src/
│   ├── assets/
│   ├── components/
│   ├── layouts/
│   ├── pages/
│   ├── routes/
│   ├── services/
│   ├── store/
│   ├── styles/
│   ├── utils/
│   └── App.jsx
│
├── package.json
└── vite.config.js
```

---

# Package Responsibilities

## common

Shared utilities used by every module.

Examples:

- Logger
- Configuration
- Constants
- Helpers

---

## indicators

Technical indicators.

Examples:

- EMA
- RSI
- ATR
- MACD
- VWAP
- Bollinger Bands

---

## trading-engine

Responsible for:

- Signal generation
- Strategy execution
- Trade lifecycle

---

## risk-engine

Responsible for:

- Position sizing
- Stop Loss
- Take Profit
- Trailing Stop
- Daily loss limits

---

## analytics

Responsible for:

- Performance metrics
- Trading statistics
- Portfolio analytics

---

## portfolio

Responsible for:

- Balances
- Positions
- Asset allocation
- P&L

---

## reporting

Responsible for:

- Daily reports
- Weekly reports
- Monthly reports
- Yearly reports

---

## paper-trading

Responsible for:

- Virtual wallet
- Simulated execution
- Strategy validation

---

## backtesting

Responsible for:

- Historical replay
- Performance evaluation
- Result comparison

---

## exchange

Responsible for:

- Bybit API
- Market data
- Orders
- Positions

---

## notifications

Responsible for:

- Email
- Telegram (future)
- In-app notifications

---

## ai

Responsible for:

- Performance analysis
- Strategy recommendations
- Future AI modules

---

# Documentation Structure

```
finoss-docs/
│
├── README.md
├── LICENSE
├── CHANGELOG.md
├── ROADMAP.md
│
├── docs/
│   ├── 01_Project_Vision.md
│   ├── 02_System_Requirements.md
│   ├── 03_System_Architecture.md
│   ├── 04_Project_Structure.md
│   ├── 05_Technology_Stack.md
│   ├── ...
│
├── diagrams/
├── assets/
├── templates/
└── examples/
```

---

# Naming Conventions

## Files

Use lowercase with underscores.

Examples:

```
market_analysis.py
risk_engine.py
paper_trading.py
```

---

## Classes

Use PascalCase.

```
TradingEngine
RiskManager
PortfolioService
```

---

## Functions

Use snake_case.

```
calculate_position_size()

execute_trade()

update_portfolio()
```

---

## Database Tables

Use plural snake_case.

Examples:

```
users
orders
positions
trades
market_data
strategies
```

---

## Environment Variables

Use uppercase.

Examples:

```
BYBIT_API_KEY
BYBIT_API_SECRET
SUPABASE_URL
SUPABASE_ANON_KEY
```

---

# Git Workflow

Main branches:

```
main
develop
feature/*
bugfix/*
hotfix/*
```

Commit example:

```
feat(trading): add EMA crossover strategy

fix(api): reconnect websocket automatically

docs: update system architecture
```

---

# Coding Standards

- Write readable code.
- Keep modules focused on one responsibility.
- Avoid duplicated logic.
- Add comments only where necessary.
- Write tests for new features.

---

# Testing Structure

```
tests/
│
├── unit/
├── integration/
├── paper/
└── backtesting/
```

---

# Security Guidelines

- Never commit `.env` files.
- Store secrets securely.
- Disable withdrawal permissions on API keys.
- Validate all external input.
- Log security events.

---

# Future Expansion

The project structure allows future additions such as:

- Binance integration
- OKX integration
- Mobile application
- AI microservices
- Cloud deployment
- Multi-user support

without requiring major architectural changes.

---

# Related Documents

- 01_Project_Vision.md
- 02_System_Requirements.md
- 03_System_Architecture.md
- 05_Technology_Stack.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0.0 | July 2026 | Initial project structure document |

---

© 2026 fin.oss Project
