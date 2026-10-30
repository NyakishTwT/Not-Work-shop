# Инструкция к движению в сторону вектора по направлению...

# 1. Запуск сервиса

```bash
docker compose up -d
```

## 2. Проверка статуса

```bash
curl http://localhost:8000/health
```

## 3. Выкат версии

```bash
APP_IMAGE=ghcr.io/nyakishtwt/not-work-shop:1.0.1 docker compose up -d
```

## 4. Процедура отката (Rollback)

```bash
APP_IMAGE=ghcr.io/nyakishtwt/not-work-shop:1.0.0 docker compose up -d
curl http://localhost:8000/health
```
