# 🐈 Kittygram API

Kittygram — это REST API для управления котами и их достижениями. Проект позволяет регистрировать пользователей, добавлять котиков с указанием цвета, года рождения и достижений, а также управлять ими через JWT-аутентификацию.

## Технологический стек

- Язык: Python 3.10+
- Фреймворк: Django 3.2 + Django REST Framework 3.12
- Аутентификация: Djoser (JWT + Bearer Token)
- База данных: SQLite (разработка)
- Документация: Browsable API (DRF)

## Как запустить проект (локально)

### 1. Клонирование репозитория

git clone https://github.com/zavalniuk217/kittygramZavalniukEgor.git
cd kittygramZavalniukEgor

### 2. Создание и активация виртуального окружения

Windows:
python -m venv env
env\Scripts\activate

Linux / macOS:
python3 -m venv env
source env/bin/activate

### 3. Установка зависимостей

pip install --upgrade pip
pip install -r requirements.txt

### 4. Настройка переменных окружения (необязательно)

Создайте файл .env в корне проекта:
SECRET_KEY=django-secure-wallet-key
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost

### 5. Выполнение миграций и запуск

python manage.py migrate
python manage.py runserver

Проект будет доступен по адресу: http://127.0.0.1:8000/

## Основные эндпоинты API

POST /auth/users/ - Регистрация пользователя
POST /auth/jwt/create/ - Получение JWT-токена
GET /cats/ - Список всех котиков
POST /cats/ - Добавить котика (требуется токен)
GET /cats/{id}/ - Получить котика по ID
PATCH /cats/{id}/ - Изменить котика (только владелец)
DELETE /cats/{id}/ - Удалить котика (только владелец)
GET /users/ - Список пользователей
GET /achievements/ - Список достижений

## Примеры запросов

Регистрация:
{"username": "kotik_lover", "password": "securepass123"}

Получение токена:
{"username": "kotik_lover", "password": "securepass123"}

Создание котика (заголовок: Authorization: Bearer <токен>):
{"name": "Барсик", "color": "white", "birth_year": 2020, "owner": 1, "achievements": [{"achievement_name": "лучший кот"}]}

Ответ сервера:
{"id": 1, "name": "Барсик", "color": "white", "birth_year": 2020, "owner": 1, "achievements": [], "age": 6}

## Безопасность и валидация

- JWT-аутентификация: доступ только для авторизованных
- Права владельца: только создатель может редактировать/удалять
- Валидация года рождения: нельзя указать год в будущем
- Цвет выбирается из списка (Gray, Black, White, Ginger, Mixed)

## Документация

После запуска: http://127.0.0.1:8000/cats/ и http://127.0.0.1:8000/users/

## Разработчик

Студент: Завальнюк Е. А.
Группа: ПИЭУ/246
Год: 2026
