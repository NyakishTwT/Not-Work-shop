# 📒 Guestbook Service

Production-ready микросервис гостевой книги на FastAPI и PostgreSQL с автоматизированным CI/CD конвейером и поддержкой версионированных релизов.

## 🚀 Стек технологий

- **Язык & Рантайм:** Python 3.12, управление зависимостями через [uv](https://github.com/astral-sh/uv)
- **Фреймворк:** FastAPI + Uvicorn
- **База данных:** PostgreSQL 16 (драйвер `psycopg 3`)
- **Конфигурация:** `pydantic-settings` (12-Factor App)
- **Контейнеризация:** Docker, Docker Compose
- **CI/CD:** GitHub Actions, линтинг (Ruff), тесты (Pytest), реестр образов (GHCR)

---

## 🛠 Быстрый старт

### 1. Клонирование и настройка окружения

```bash
git clone https://github.com/NyakishTwT/Not-Work-shop.git
cd Not-Work-shop
cp .env.example .env
```

### 2. Запуск через Docker Compose (локально)

```bash
docker compose up -d --build
```

Сервис будет доступен по адресу: `http://localhost:8000`

---

## 📡 API Эндпоинты

- `GET /` — приветственное сообщение (настраивается через `GREETING`)
- `GET /health` — проверка работоспособности сервиса (healthcheck)
- `GET /messages` — получить список всех сообщений
- `POST /messages` — добавить сообщение (JSON: `{"author": "string", "text": "string"}`)

---

## 🔄 CI/CD и релизы

В проекте настроен автоматический конвейер (GitHub Actions):

1. **CI (`check`):** При каждом `push` и `pull_request` запускаются линтер `ruff` и тесты `pytest`.
2. **CD (`build-and-push`):**
   - При пуше в ветку `main` собирается и публикуется образ с тегом `:latest`.
   - При пуше Git-тега по SemVer (`vX.Y.Z`) собирается версионированный образ в GitHub Container Registry (`ghcr.io`).

---

## 📖 Эксплуатация и документация

- [RUNBOOK.md](./RUNBOOK.md) — аварийные инструкции, мониторинг и регламент отката (Rollback).
- [CHANGELOG.md](./CHANGELOG.md) — история версий и изменений проекта.
