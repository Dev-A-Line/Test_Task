
# Тестовое задание на позицию Middle Backend Специалиста

Цель тестового задания - разработать API для приложения знакомств. Ваша задача - создать два основных эндпоинта: `user` и `match`.

## Эндпоинты:

### 1. User

- `GET /users`: Возвращает список всех пользователей. Должен поддерживать сортировку по `username`, `email`, и фильтрацию по `age` и `location`.

    Ответ:
    ```json
    {
        "users": [
            {
                "id": 1,
                "username": "user1",
                "email": "user1@example.com",
                "age": 25,
                "location": "Moscow"
            },
            {
                "id": 2,
                "username": "user2",
                "email": "user2@example.com",
                "age": 28,
                "location": "St. Petersburg"
            }
        ]
    }
    ```

- `POST /users`: Создает нового пользователя. Принимает JSON с полями `username`, `email`, `password`, `age`, `location`.

    Запрос:
    ```json
    {
        "username": "newuser",
        "email": "newuser@example.com",
        "password": "securepassword",
        "age": 30,
        "location": "Kazan"
    }
    ```
    Ответ:
    ```json
    {
        "id": 3,
        "username": "newuser",
        "email": "newuser@example.com",
        "age": 30,
        "location": "Kazan"
    }
    ```

- `GET /users/{user_id}`: Возвращает детали пользователя по ID.

    Ответ:
    ```json
    {
        "id": 1,
        "username": "user1",
        "email": "user1@example.com",
        "age": 25,
        "location": "Moscow"
    }
    ```

- `PUT /users/{user_id}`: Обновляет детали пользователя по ID.

    Запрос:
    ```json
    {
        "username": "updateduser",
        "email": "updateduser@example.com",
        "age": 31,
        "location": "Ufa"
    }
    ```
    Ответ:
    ```json
    {
        "id": 1,
        "username": "updateduser",
        "email": "updateduser@example.com",
        "age": 31,
        "location": "Ufa"
    }
    ```

- `DELETE /users/{user_id}`: Удаляет пользователя по ID.

    Ответ:
    ```json
    {
        "message": "User successfully deleted"
    }
    ```

### 2. Match

- `GET /matches`: Возвращает список всех совпадений (пар пользователей). Поддерживает сортировку по дате совпадения.

    Ответ:
    ```json
    {
        "matches": [
            {
                "id": 1,
                "user1_id": 1,
                "user2_id": 2,
                "match_date": "2023-07-05"
            },
            {
                "id": 2,
                "user1_id": 1,
                "user2_id": 3,
                "match_date": "2023-07-06"
            }
        ]
    }
    ```

- `POST /matches`: Создает новое совпадение. Принимает JSON с полями `user1_id`, `user2_id`.

    Запрос:
    ```json
    {
        "user1_id": 1,
        "user2_id": 3
    }
    ```
    Ответ:
    ```json
    {
        "id": 3,
        "user1_id": 1,
        "user2_id": 3,
        "match_date": "2023-07-07"
    }
    ```

- `DELETE /matches/{match_id}`: Удаляет совпадение по ID.

    Ответ:
    ```json
    {
        "message": "Match successfully deleted"
    }
    ```

## Требования:

- Используйте FastAPI для создания веб-сервера.
- SQLAlchemy для работы с базой данных.
- Создайте модели данных для SQLAlchemy с использованием алхимического ORM.
- Создайте аутентификацию и авторизацию для эндпоинтов.
- Напишите тесты для каждого эндпоинта.
- Реализуйте обработку ошибок.
- Реализуйте фильтрацию и сортировку для соответствующих эндпоинтов.

## Дополнительные задачи:

- Создайте Dockerfile для контейнеризации приложения.
- Напишите документацию с помощью Swagger.
- Реализуйте автоматическое развертывание и тестирование с использованием CI/CD.(Можно использовать Vercel, Heroku или любой другой удобный для вас сервис.)
