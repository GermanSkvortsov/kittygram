# Kittygram

Социальная сеть для обмена фотографиями любимых питомцев. Учебный проект, выполненный в рамках прохождения курса «Python-разработчик» в Яндекс Практикуме.

## Описание

Kittygram — это веб-приложение, где пользователи могут регистрироваться, публиковать фотографии своих питомцев, редактировать и удалять свои записи, а также просматривать публикации других пользователей.

Проект развёрнут в Docker-контейнерах с автоматическим деплоем через GitHub Actions.

## Функциональность

- Регистрация и авторизация пользователей

- Добавление, редактирование и удаление записей о питомцах

- Загрузка фотографий

- Просмотр публикаций других пользователей

- Административная панель Django

## Технологии

- Python 3.12

- Django

- Django REST Framework

- PostgreSQL

- Docker

- Docker Compose

- Nginx

- React (фронтенд)

- GitHub Actions (CI/CD)

## Архитектура

Проект состоит из четырёх контейнеров:

- db — PostgreSQL

- backend — Django + Gunicorn

- frontend — React (сборка статики)

- gateway — Nginx

Данные сохраняются в volumes:

- pg_data — данные PostgreSQL

- static — статика бэкенда и фронтенда

- media — загруженные пользователями изображения

## Установка и запуск

1. Клонируйте репозиторий:

```bash
git clone https://github.com/GermanSkvortsov/kittygram.git
```

2. Создайте файл .env по образцу .env.example

3. Запустите контейнеры:

```bash
docker compose up -d --build
```

4. Выполните миграции и соберите статику:

```bash
docker compose exec backend python manage.py migrate
docker compose exec backend python manage.py collectstatic --noinput
```

Проект будет доступен по адресу: http://localhost:9000

## CI/CD

При пуше в ветку main GitHub Actions автоматически:

- запускает тесты

- собирает образы

- отправляет их на Docker Hub

- обновляет контейнеры на сервере

- уведомляет о деплое в Telegram

## Тестирование

Для запуска тестов выполните:

```bash
pytest
```

## Автор

Герман Скворцов

[Мой GitHub](https://github.com/GermanSkvortsov)
