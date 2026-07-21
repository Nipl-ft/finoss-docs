# Supabase Architecture

| Field | Value |
|-------|-------|
| Project | fin.oss (Financial Operating System) |
| Document | 07_Supabase_Architecture.md |
| Version | 1.0.0 |
| Status | Draft |
| Repository | finoss-docs |
| Related Documents | 06_Database_Design.md, 08_Bybit_API_Integration.md |

---

# Executive Summary

Supabase is the primary Backend-as-a-Service (BaaS) platform for **fin.oss**.

It provides:

- PostgreSQL Database
- User Authentication
- Row-Level Security (RLS)
- Realtime Database Events
- File Storage
- Edge Functions (Future)
- Database Backups
- REST & Realtime APIs

Supabase serves as the central data platform, while the FastAPI backend handles business logic, trading decisions, and communication with Bybit.

---

# Objectives

The Supabase architecture is designed to provide:

- Secure authentication
- Reliable PostgreSQL database
- Fine-grained access control
- Real-time synchronization
- High availability
- Easy scalability
- Simplified development

---

# High-Level Architecture

```
                    User
                      │
                      ▼
             React Frontend
                      │
        ┌─────────────┴─────────────┐
        │                           │
        ▼                           ▼
 Supabase Auth                FastAPI Backend
        │                           │
        └─────────────┬─────────────┘
                      ▼
              PostgreSQL Database
                      │
        ┌─────────────┼─────────────┐
        │             │             │
        ▼             ▼             ▼
   Realtime       Storage      Edge Functions
                                     │
                                     ▼
                              Bybit Integration
```

---

# Responsibilities

## Supabase

Responsible for:

- User authentication
- PostgreSQL database
- Data storage
- Row-Level Security
- Realtime subscriptions
- File storage
- Database backups

---

## FastAPI Backend

Responsible for:

- Business logic
- Trading engine
- Risk management
- Strategy execution
- Market analysis
- Bybit API communication
- AI integration

---

## React Frontend

Responsible for:

- User interface
- Dashboard
- Portfolio visualization
- Charts
- Reports
- Settings

---

# Authentication Architecture

Authentication is handled by Supabase Auth.

Supported methods:

- Email & Password
- Password Reset
- Email Verification

Future options:

- Google OAuth
- GitHub OAuth
- Multi-factor Authentication (MFA)

---

# User Flow

```
User Login
      │
      ▼
Supabase Auth
      │
      ▼
JWT Token
      │
      ▼
FastAPI Backend
      │
      ▼
Protected API Endpoints
```

---

# Database Organization

The PostgreSQL database stores:

## User Data

- Profiles
- Preferences
- Sessions

---

## Exchange Data

- API Keys
- Exchange Configuration

---

## Market Data

- Candles
- Trades
- Funding Rates
- Open Interest
- Mark Prices

---

## Trading Data

- Orders
- Positions
- Executions
- Trade History

---

## Portfolio Data

- Wallets
- Balances
- Snapshots

---

## Analytics

- Reports
- Performance Metrics
- Logs

---

# Row-Level Security (RLS)

RLS must be enabled on all user-owned tables.

Example policy:

- Users can only access their own records.
- Users cannot view other users' data.
- API keys are restricted to the owner.
- Audit logs are append-only.

---

# Storage

Supabase Storage will be used for:

- User avatars
- Strategy import/export files
- Backtest reports
- CSV exports
- Future AI datasets

---

# Realtime

Realtime subscriptions provide live updates for:

- Portfolio balances
- Open positions
- Order status
- Trade execution
- Dashboard notifications

This reduces the need for constant polling.

---

# Edge Functions (Future)

Planned uses:

- Scheduled maintenance tasks
- Report generation
- Notification delivery
- AI preprocessing
- Data cleanup

Trading logic will remain in the FastAPI backend.

---

# Secrets Management

Sensitive values must never be exposed to the frontend.

Examples:

- Bybit API Secret
- JWT Secret
- Service Role Key

Use environment variables for all secrets.

---

# Security Model

Authentication:
- Supabase Auth

Authorization:
- Row-Level Security

Encryption:
- HTTPS
- Encrypted API secrets
- Secure JWT handling

Logging:
- Audit logs
- Authentication events
- API access logs

---

# Backup Strategy

- Automated daily backups
- Point-in-time recovery (where supported)
- Regular backup verification
- Restore testing

---

# Monitoring

Monitor:

- Database performance
- Authentication activity
- API usage
- Error logs
- Storage utilization

Future:

- Grafana dashboards
- Prometheus metrics

---

# Development Workflow

1. Design schema
2. Create migration
3. Apply to Supabase
4. Test RLS
5. Connect FastAPI
6. Connect React
7. Validate functionality

---

# Future Expansion

The architecture supports:

- Multiple exchanges
- Mobile applications
- AI services
- Additional storage
- Advanced analytics
- Distributed microservices

without major redesign.

---

# Related Documents

- 06_Database_Design.md
- 08_Bybit_API_Integration.md
- 17_Dashboard_Design.md
- 18_Security_Guidelines.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0.0 | July 2026 | Initial Supabase architecture document |

---

© 2026 fin.oss Project
