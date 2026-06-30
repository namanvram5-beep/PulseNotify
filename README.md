# PulseNotify

PulseNotify is a Django REST Framework application that allows users to create flight price alerts. The application periodically checks flight prices using Celery and Redis, and notifies users when the configured threshold price is reached.

---

## Features

- User Registration
- JWT Authentication
- Create Flight Price Alerts
- List User Alerts
- Delete Alerts
- Mock Flight Price API
- Background Price Checking using Celery
- Redis Message Broker
- Django Admin
- Notification Logging

---

## Tech Stack

- Python 3.14
- Django 6
- Django REST Framework
- JWT Authentication
- Celery
- Redis
- PostgreSQL
- Docker
- Docker Compose

---

## Installation

Clone the repository

```bash
git clone <repository-url>
cd PulseNotify
```

Create virtual environment

```bash
python -m venv .venv
```

Activate

Windows

```bash
.venv\Scripts\activate
```

Linux

```bash
source .venv/bin/activate
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

## Environment Variables

Create

```
.env
```

Refer to `.env.example`

---

## Run Redis

Linux

```bash
redis-server
```

or

```bash
sudo systemctl start redis
```

---

## Apply Migrations

```bash
python manage.py migrate
```

Create admin

```bash
python manage.py createsuperuser
```

---

## Run Django

```bash
python manage.py runserver
```

---

## Run Celery Worker

```bash
celery -A config worker -l info
```

---

## Run Celery Beat

```bash
celery -A config beat -l info
```

---

## Docker

```bash
docker compose build
docker compose up
```

---

## API Endpoints

### Authentication

POST

```
/api/auth/register/
```

POST

```
/api/auth/login/
```

---

### Alerts

POST

```
/api/alerts/
```

GET

```
/api/alerts/
```

DELETE

```
/api/alerts/<id>/
```

---

### Flight API

GET

```
/api/flights/price/?route=DEL-BOM
```

---

### Admin

GET

```
/api/admin/summary/
```

---

## Running Tests

```bash
python manage.py test
```

---

## Project Structure

```
PulseNotify/

accounts/
alerts/
config/

Dockerfile
docker-compose.yml
requirements.txt
README.md
Design.md
manage.py
