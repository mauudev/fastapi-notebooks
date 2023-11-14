# FastAPI + SQLAlchemy 2.0 Asyncio extension

A simple API Rest project using the Asyncio extension of SQLAlchemy 2.0 with FastAPI.

# Setup

## Install

```shell
$ python3 -m venv venv
$ . venv/bin/activate
(venv) $ pip install -r requirements.lock
```

## Database setup

```shell
(venv) $ docker run -d --name db \
  -e POSTGRES_PASSWORD=password \
  -e PGDATA=/var/lib/postgresql/data/pgdata \
  -v pgdata:/var/lib/postgresql/data/pgdata \
  -p 5432:5432 \
  postgres:15.2-alpine

# Cleanup database
# $ docker stop db
# $ docker rm db
# $ docker volume rm pgdata

(venv) $ alembic upgrade head
```

# Run

```shell
(venv) $ uvicorn app.main:app --reload --reload-dir app
```

Then go to [localhost:8000/docs](http://localhost:8000/docs) to see the API documentation.

# Test

```shell
(venv) $ pip install -r requirements_test.txt
(venv) $ black app
(venv) $ ruff app
(venv) $ mypy app
(venv) $ pytest app
```
