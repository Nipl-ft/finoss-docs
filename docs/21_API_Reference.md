# API Reference

| Field | Value |
|-------|-------|
| Project | fin.oss (Financial Operating System) |
| Document | 21_API_Reference.md |
| Version | 1.0.0 |
| Status | Draft |
| Repository | finoss-docs |
| Last Updated | July 2026 |

---

# Table of Contents

1. Executive Summary
2. API Standards
3. Authentication
4. API Versioning
5. Common Response Format
6. Authentication APIs
7. Market APIs
8. Portfolio APIs
9. Strategy APIs
10. Paper Trading APIs
11. Backtesting APIs
12. AI APIs
13. Settings APIs
14. Error Codes
15. Rate Limiting
16. Future APIs
17. Revision History

---

# 1. Executive Summary

The fin.oss API enables secure communication between the frontend and backend.

Features:

- REST API
- JSON format
- JWT authentication
- Versioned endpoints
- Consistent error handling

---

# 2. API Standards

Base URL

/api/v1

Content Type

application/json

HTTP Methods

GET

Retrieve data

POST

Create resources

PUT

Replace resources

PATCH

Update resources

DELETE

Remove resources

---

# 3. Authentication

Authentication uses:

Supabase JWT

Authorization Header

Authorization: Bearer <JWT_TOKEN>

Every protected endpoint requires a valid JWT.

---

# 4. API Versioning

Current version

/api/v1

Future versions

/api/v2

Older versions remain supported for a defined period before deprecation.

---

# 5. Common Response Format

Success

{
  "success": true,
  "data": {},
  "message": "Request completed"
}

Error

{
  "success": false,
  "error": {
      "code": "INVALID_REQUEST",
      "message": "Invalid parameters"
  }
}

---

# 6. Authentication APIs

POST

/auth/login

POST

/auth/logout

POST

/auth/refresh

GET

/auth/me

POST

/auth/reset-password

---

# 7. Market APIs

GET

/markets

GET

/markets/{symbol}

GET

/markets/{symbol}/candles

GET

/markets/{symbol}/ticker

GET

/markets/{symbol}/orderbook

GET

/markets/{symbol}/trades

---

# 8. Portfolio APIs

GET

/portfolio

GET

/portfolio/balance

GET

/portfolio/positions

GET

/portfolio/history

---

# 9. Strategy APIs

GET

/strategies

POST

/strategies

PUT

/strategies/{id}

DELETE

/strategies/{id}

POST

/strategies/{id}/enable

POST

/strategies/{id}/disable

---

# 10. Paper Trading APIs

GET

/paper/account

GET

/paper/orders

GET

/paper/positions

POST

/paper/reset

---

# 11. Backtesting APIs

POST

/backtest/run

GET

/backtest/results

GET

/backtest/{id}

DELETE

/backtest/{id}

---

# 12. AI APIs

GET

/ai/summary

GET

/ai/insights

GET

/ai/trade-review/{id}

GET

/ai/strategy-review/{id}

---

# 13. Settings APIs

GET

/settings

PUT

/settings

GET

/settings/risk

PUT

/settings/risk

GET

/settings/profile

PUT

/settings/profile

---

# 14. Error Codes

400

Bad Request

401

Unauthorized

403

Forbidden

404

Not Found

409

Conflict

422

Validation Error

429

Too Many Requests

500

Internal Server Error

503

Service Unavailable

---

# 15. Rate Limiting

Recommended limits:

Authenticated users:

120 requests/minute

Public endpoints:

60 requests/minute

Sensitive endpoints may have lower limits.

---

# 16. Future APIs

Future endpoints may include:

News

Sentiment

Multi-exchange

Webhook support

Mobile API

---

# 17. Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0.0 | July 2026 | Initial API Reference |

---

© 2026 fin.oss Project
