# Быстрый старт с Docker

## 1. Подготовка

```bash
# Создать .env файл
cp .env.example .env

# Отредактировать .env - изменить SECRET_KEY, DB_PASSWORD, ALLOWED_HOSTS, STRIPE ключи
nano .env
```

## 2. Подготовка SSL сертификатов

```bash
# Создать директорию для SSL
mkdir -p ssl

# Скопировать ваши сертификаты
cp /path/to/fullchain.pem ssl/
cp /path/to/privkey.pem ssl/

# Обновить docker-compose.yml, заменить volume ssl_certs на:
# - ./ssl:/etc/nginx/ssl:ro
```

## 3. Запуск

```bash
# Собрать и запустить все контейнеры
docker-compose up -d --build

# Проверить статус
docker-compose ps

# Создать суперпользователя
docker-compose exec web python manage.py createsuperuser
```

## 4. Доступ

- Сайт: https://domen.com
- Админка: https://domen.com/admin

## Основные команды

```bash
# Просмотр логов
docker-compose logs -f

# Остановка
docker-compose stop

# Перезапуск
docker-compose restart

# Остановка и удаление
docker-compose down

# Вход в контейнер
docker-compose exec web bash

# Миграции
docker-compose exec web python manage.py migrate

# Тесты
docker-compose exec web python manage.py test
```

Подробная документация: `DOCKER_DEPLOY.md`
