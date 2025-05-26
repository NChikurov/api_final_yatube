# API для социальной сети Yatube

API для социальной сети Yatube, где пользователи могут публиковать посты, подписываться на других пользователей, комментировать посты и создавать группы по интересам.

## Функциональность

- Регистрация и аутентификация пользователей
- Создание, редактирование и удаление постов
- Создание и управление группами
- Комментирование постов
- Подписка на других пользователей
- Пагинация и фильтрация данных
- Загрузка изображений к постам

## Технологии

- Python 3.7+
- Django 3.2.16
- Django REST Framework 3.12.4
- Simple JWT 4.7.2
- Pillow 11.0.0
- PyJWT 2.1.0
- pytest 6.2.4
- Djoser 2.1.0

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```bash
git clone https://github.com/yandex-praktikum/api_final_yatube.git
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```bash
python -m venv venv
source venv/Scripts/activate  # для Windows
source venv/bin/activate      # для Linux/Mac
```

Установить зависимости из файла requirements.txt:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Выполнить миграции:

```bash
python manage.py migrate
```

Запустить проект:

```bash
python manage.py runserver
```

## API Endpoints

### Аутентификация

Получение токена:
```http
POST /api/v1/jwt/create/
Content-Type: application/json

{
    "username": "string",
    "password": "string"
}
```

Обновление токена:
```http
POST /api/v1/jwt/refresh/
Content-Type: application/json

{
    "refresh": "string"
}
```

### Посты

Получение списка постов:
```http
GET /api/v1/posts/
Authorization: Bearer <token>
```

Создание поста:
```http
POST /api/v1/posts/
Authorization: Bearer <token>
Content-Type: application/json

{
    "text": "string",
    "group": 1,
    "image": "string"
}
```

### Группы

Получение списка групп:
```http
GET /api/v1/groups/
Authorization: Bearer <token>
```

### Подписки

Получение списка подписок:
```http
GET /api/v1/follow/
Authorization: Bearer <token>
```

Создание подписки:
```http
POST /api/v1/follow/
Authorization: Bearer <token>
Content-Type: application/json

{
    "following": "string"
}
```

### Комментарии

Получение комментариев к посту:
```http
GET /api/v1/posts/{post_id}/comments/
Authorization: Bearer <token>
```

Создание комментария:
```http
POST /api/v1/posts/{post_id}/comments/
Authorization: Bearer <token>
Content-Type: application/json

{
    "text": "string"
}
```

## Автор

Проект разработан в рамках обучения на платформе Яндекс.Практикум.
