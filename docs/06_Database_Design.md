# Database Design

| Field | Value |
|-------|-------|
| Project | fin.oss (Financial Operating System) |
| Document | 06_Database_Design.md |
| Version | 1.0.0 |
| Status | Draft |
| Repository | finoss-docs |
| Database | PostgreSQL (Supabase) |
| Author | Project Owner |
| Last Updated | July 2026 |

---

# Table of Contents

1. Executive Summary
2. Purpose
3. Scope
4. Database Objectives
5. Design Principles
6. Database Architecture
7. Database Layers
8. Naming Conventions
9. Data Standards
10. Audit Standards
11. Security Standards
12. Backup & Recovery
13. Future Expansion
14. Revision History

---

# 1. Executive Summary

The fin.oss database is the core of the platform.

Every trading activity, market event, portfolio update, strategy execution, report, and AI analysis depends on the database.

The database is designed using PostgreSQL through Supabase and follows modern relational database principles to ensure:

- High reliability
- Data integrity
- Scalability
- Security
- Performance
- Maintainability

The schema is normalized to reduce redundancy while allowing future expansion without major redesign.

---

# 2. Purpose

This document defines:

- Database architecture
- Table standards
- Naming conventions
- Relationships
- Security
- Data integrity
- Performance strategy

It serves as the blueprint for implementing the Supabase database.

---

# 3. Scope

Version 1.0 includes support for:

- Authentication
- User profiles
- Exchange configuration
- Market data
- Technical indicators
- Trading
- Portfolio
- Risk management
- Paper trading
- Backtesting
- Reports
- Logs

Future versions will include:

- AI learning
- News analysis
- Market sentiment
- Multi-exchange support
- Mobile synchronization

---

# 4. Database Objectives

The database must:

- Store all trading information
- Preserve historical data
- Support fast queries
- Ensure data consistency
- Support future AI learning
- Support audit trails
- Protect sensitive information

---

# 5. Design Principles

## 5.1 Normalization

Tables will generally follow Third Normal Form (3NF) to minimize redundancy while balancing performance.

---

## 5.2 Single Source of Truth

Each data item should have one authoritative location.

Example:

- Users stored only in `profiles`
- Orders stored only in `orders`
- Positions stored only in `positions`

---

## 5.3 Modularity

Each business domain has its own group of tables.

Domains include:

- Authentication
- Market Data
- Trading
- Portfolio
- Risk
- Analytics
- Paper Trading
- Backtesting

---

## 5.4 Scalability

The schema must support:

- Additional exchanges
- Additional strategies
- More assets
- More indicators
- AI modules

without redesign.

---

## 5.5 Security

Sensitive information must never be exposed.

Examples:

- API secrets
- Authentication tokens
- Personal settings

---

# 6. Database Architecture

```
                    Frontend
                       │
                       ▼
                  FastAPI Backend
                       │
                       ▼
               PostgreSQL (Supabase)
                       │
       ┌───────────────┼───────────────┐
       │               │               │
 Authentication   Trading Data   Market Data
       │               │               │
       └───────────────┼───────────────┘
                       │
                   Analytics
```

The frontend never accesses trading tables directly. All trading operations go through the backend.

---

# 7. Database Layers

## Layer 1 – Authentication

Stores:

- Users
- Profiles
- Sessions
- Preferences

---

## Layer 2 – Market Data

Stores:

- Symbols
- Candles
- Trades
- Order books
- Funding rates
- Open interest

---

## Layer 3 – Trading

Stores:

- Orders
- Positions
- Executions
- Signals

---

## Layer 4 – Portfolio

Stores:

- Wallets
- Balances
- Portfolio snapshots
- Performance

---

## Layer 5 – Analytics

Stores:

- Reports
- Metrics
- Statistics

---

## Layer 6 – AI (Future)

Stores:

- Predictions
- Recommendations
- Learning history

---

# 8. Naming Conventions

## Tables

Use plural snake_case.

Examples:

```
users
profiles
orders
positions
trades
market_data
```

---

## Columns

Use snake_case.

Examples:

```
created_at
updated_at
order_status
entry_price
```

---

## Primary Keys

Every table uses:

```
id UUID PRIMARY KEY
```

---

## Foreign Keys

Format:

```
user_id
order_id
position_id
symbol_id
strategy_id
```

---

## Boolean Columns

Prefix with:

```
is_
has_
```

Examples:

```
is_active
is_deleted
has_position
```

---

## Timestamp Columns

Every table should include:

```
created_at
updated_at
```

Optional:

```
deleted_at
```

---

# 9. Standard Data Types

| Purpose | Type |
|----------|------|
| ID | UUID |
| Name | TEXT |
| Description | TEXT |
| Price | NUMERIC(20,8) |
| Quantity | NUMERIC(20,8) |
| Percentage | NUMERIC(10,4) |
| Boolean | BOOLEAN |
| Date | DATE |
| Timestamp | TIMESTAMPTZ |
| JSON Data | JSONB |

---

# 10. Audit Fields

Most tables include:

```sql
id UUID PRIMARY KEY
created_at TIMESTAMPTZ
updated_at TIMESTAMPTZ
created_by UUID
updated_by UUID
```

Optional:

```sql
deleted_at TIMESTAMPTZ
```

---

# 11. Security Standards

The database will implement:

- Row-Level Security (RLS)
- Least privilege access
- Encrypted connections
- Secure authentication
- API key protection

Secrets are **never** stored in plaintext.

---

# 12. Backup & Recovery

Backup strategy:

- Daily automated backups
- Point-in-time recovery (where available)
- Weekly validation of backups
- Regular restore testing

---

# 13. Future Expansion

The database is designed to support:

- Multiple exchanges
- AI-generated insights
- News sentiment
- Mobile synchronization
- Multi-account management
- Advanced analytics

without major structural changes.

---

# Next Chapters

The following parts of this document will define:

- User & Authentication tables
- Market Data tables
- Trading tables
- Portfolio tables
- Risk Management tables
- Paper Trading
- Backtesting
- AI
- ER diagrams
- SQL implementation

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0.0 | July 2026 | Database Architecture & Standards |

---

© 2026 fin.oss Project
