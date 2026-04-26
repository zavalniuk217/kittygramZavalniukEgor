# 🐈 Kittygram API

**Kittygram** — это REST API для управления котиками и их достижениями. Проект позволяет регистрировать пользователей, добавлять котиков с указанием цвета, года рождения и достижений, а также управлять ими через JWT-аутентификацию.

---

## Технологический стек

- **Язык:** Python 3.10+
- **Фреймворк:** Django 3.2 + Django REST Framework 3.12
- **Аутентификация:** Djoser (JWT + Bearer Token)
- **База данных:** SQLite (разработка)
- **Документация:** Browsable API (DRF)

---

## Как запустить проект (локально)

### 1. Клонирование репозитория

```bash
git clone https://github.com/zavalniuk217/kittygramZavalniukEgor.git
cd kittygramZavalniukEgor
2. Создание и активация виртуального окружения
Windows:

bash
python -m venv env
env\Scripts\activate
Linux / macOS:

bash
python3 -m venv env
source env/bin/activate
3. Установка зависимостей
bash
pip install --upgrade pip
pip install -r requirements.txt
4. Настройка переменных окружения (необязательно)
Создайте файл .env в корне проекта (можно скопировать из .env.example):

SECRET_KEY=django-insecure-ваш-секретный-ключ
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost
5. Выполнение миграций и запуск
bash
python manage.py migrate
python manage.py runserver
Проект будет доступен по адресу: http://127.0.0.1:8000/

Основные эндпоинты API
Метод	Эндпоинт	Описание
POST	/auth/users/	Регистрация пользователя
POST	/auth/jwt/create/	Получение JWT-токена
GET	/cats/	Список всех котиков
POST	/cats/	Добавить котика (требуется токен)
PATCH	/cats/{id}/	Изменить котика (только владелец)
DELETE	/cats/{id}/	Удалить котика (только владелец)
GET	/users/	Список пользователей
GET	/achievements/	Список достижений

Примеры запросов (JSON)
Регистрация пользователя
json
POST /auth/users/
{
    "username": "kotik_lover",
    "password": "securepass123"
}
Получение JWT-токена
json
POST /auth/jwt/create/
{
    "username": "kotik_lover",
    "password": "securepass123"
}
Создание котика (требуется токен)
Заголовок: Authorization: Bearer <ваш_токен>

json
POST /cats/
{
    "name": "Барсик",
    "color": "White",
    "birth_year": 2020,
    "owner": 1,
    "achievements": [{"achievement_name": "Лучший кот"}]
}
Ответ:

json
{
    "id": 1,
    "name": "Барсик",
    "color": "White",
    "birth_year": 2020,
    "owner": 1,
    "achievements": [],
    "age": 6
}
Безопасность и валидация
JWT-аутентификация: Доступ к созданию и изменению котиков есть только у авторизованных пользователей.

Права владельца: Редактировать и удалять котика может только тот пользователь, который его добавил.

Валидация года рождения: Нельзя указать год в будущем.

Цвет: Выбор из предопределённого списка (Gray, Black, White, Ginger, Mixed).

Документация API
После запуска проекта документация доступна встроенными средствами DRF (Browsable API):

http://127.0.0.1:8000/cats/

http://127.0.0.1:8000/users/

Разработчик
Студент: Завальнюк Е. А.
Группа: ПИ2у/24б
Год: 2026
