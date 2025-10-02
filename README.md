**Kittygram** — это веб-приложение для публикации и просмотра анкет любимых питомцев.  
Каждый пользователь может зарегистрироваться, добавить карточки со своими питомцами, указывать достижения и просматривать других котиков.

Развёрнутое приложение: [https://kittygram-learning.ru/](https://kittygram-learning.ru/)

---

## Используемые технологии

### Backend
- Python 3.12
- Django
- Django REST Framework
- Gunicorn
- PostgreSQL 13

### Frontend
- React
- Node.js 18
- npm

### Инфраструктура
- Docker + Docker Compose
- Nginx
- GitHub Actions (CI/CD)
- appleboy actions (scp, ssh, telegram)

---

## Необходимые инструменты

Для локального запуска и деплоя проекта понадобятся:
- Python 3.12
- Node.js 18
- Docker и Docker Compose
- PostgreSQL (если запускать не в контейнере)
- Git

---

## Установка и запуск

### 1. Клонировать репозиторий
```bash
git clone https://github.com/ilyak475/kittygram_final
cd kittygram
```

### 2. Создать .env файл
```
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_HOST=db
DB_PORT=5432
SECRET_KEY='your_secret_key'
DEBUG=False
ALLOWED_HOSTS=localhost,127.0.0.1,kittygram-learning.ru
EXTERNAL_PORT=8000
```
### 3. Запуск в Docker
```bash
docker compose -f docker-compose.production.yml up -d
```
После запуска будут доступны:

- Backend (API) — http://localhost:8000/api/

- Frontend — http://localhost:8000/

- Админ-панель Django — http://localhost:8000/admin/

### 4. Применение миграций и сборка статики
```
docker compose -f docker-compose.production.yml exec backend python manage.py migrate --noinput
```
```
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic --noinput
```

## CI/CD

Проект настроен на автоматическую сборку и деплой через GitHub Actions:

- Запускаются тесты (flake8 и Django tests)

- Собираются образы backend, frontend и gateway и пушатся в Docker Hub

- Выполняется деплой на сервер через ssh и scp

- После успешного деплоя отправляется уведомление в Telegram

Проект выполнен в рамках обучения и практики.

Автор: Кравченко Илья
GitHub: [IlyaK1V](https://github.com/IlyaK1V/)