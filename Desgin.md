# PulseNotify Design Document

---

## Overview

PulseNotify allows users to create flight price alerts.

A background scheduler periodically checks mocked flight prices and generates notifications when prices fall below configured thresholds.

---

## Architecture

```
Client
    │
    ▼
Django REST API
    │
    ▼
SQLite/PostgreSQL
    │
    ▼
Celery
    │
Redis Broker
    │
Celery Beat
    │
Price Checker
    │
Notification Generator
```

---

## Components

### Accounts

- Registration
- Login
- JWT Authentication

---

### Alerts

Stores

- Origin
- Destination
- Threshold Price
- Status

---

### Notification Log

Stores

- Triggered Alert
- Triggered Price
- Timestamp
- Message

---

### Celery

Runs every 60 seconds.

Workflow

```
Beat

↓

check_prices()

↓

Mock Flight API

↓

Compare Threshold

↓

send_notification()

↓

NotificationLog
```

---

## Database

### User

Default Django User

---

### UserProfile

- User
- Role

---

### PriceAlert

- User
- Origin
- Destination
- Threshold
- Status
- Created At

---

### NotificationLog

- Alert
- Triggered Price
- Message
- Created At

---

## Authentication

JWT

Login

↓

Access Token

↓

Authorization Header

↓

Protected APIs

---

## API Flow

Register

↓

Login

↓

Receive JWT

↓

Create Alert

↓

Background Task

↓

Notification Generated

---

## Assumptions

- Flight prices are mocked.
- Notification is stored in database.
- Email/SMS integration not implemented.
- One notification per alert.

---

## Future Improvements

- Email Notifications
- SMS Notifications
- Real Flight APIs
- Kafka Event Streaming
- WebSocket Live Updates
- Kubernetes Deployment
- CI/CD Pipeline
