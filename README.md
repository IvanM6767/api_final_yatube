# API для Yatube

[![Python](https://img.shields.io/badge/-Python-464641?style=flat-square&logo=Python)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-464646?style=flat-square&logo=django)](https://www.djangoproject.com/)
[![Pytest](https://img.shields.io/badge/Pytest-464646?style=flat-square&logo=pytest)](https://docs.pytest.org/en/6.2.x/)
[![Postman](https://img.shields.io/badge/Postman-464646?style=flat-square&logo=postman)](https://www.postman.com/)

## Описание

Яндекс Практикум. Спринт 9. Итоговый проект. API для Yatube.

## Функционал

- Подписка и отписка от авторизованного пользователя;
- Авторизованный пользователь просматривает посты, создавёт новые, удаляет и изменяет их;
- Просмотр сообществ;
- Комментирование, просмотр, удаление и обновление комментариев;
- Фльтрация по полям.

## Установка

1. Клонировать репозиторий:

   ```python
   git clone git@github.com:IvanM6767/api_final_yatube.git
   ```

2. Перейти в папку с проектом:

   ```python
   cd api_final_yatube/
   ```

3. Установить виртуальное окружение для проекта:

   ```python
   python -m venv venv
   ```

4. Активировать виртуальное окружение для проекта:

   ```python
   source venv/Scripts/activate
   ```

5. Установить зависимости:

   ```python
   python3 -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

6. Выполнить миграции на уровне проекта:

   ```python
   cd yatube
   python3 manage.py makemigrations
   python3 manage.py migrate
   ```

7. Запустить проект:

   `python manage.py runserver`

## Примеры запросов

Получение токена

Отправить POST-запрос на адрес `api/v1/jwt/create/` и передать 2 поля в `data`:

1. `username` - имя пользователя.
2. `password` - пароль пользователя.

Создание поста

Отправить POST-запрос на адрес `api/v1/posts/` и передать обязательное поле `text`, в заголовке указать `Authorization`:`Bearer <токен>`.

1. Пример запроса:

   ```json
   {
     "text": "1 post."
   }
   ```

2. Пример ответа:

   ```json
   {
     "id": 2,
     "author": "Alex",
     "text": "1 post.",
     "pub_date": "2023-04-03T14:34:14.144814Z",
     "image": null,
     "group": null
   }
   ```

Комментирование поста пользователя

Отправить POST-запрос на адрес `api/v1/posts/{post_id}/comments/` и передать обязательные поля `post` и `text`, в заголовке указать `Authorization`:`Bearer <токен>`.

1. Пример запроса:

   ```json
   {
     "post": 1,
     "text": "Text"
   }
   ```

2. Пример ответа:

   ```json
   {
     "id": 1,
     "author": "Ivan",
     "text": "Теxt",
     "created": "2023-03-03T13:33:13.148814Z",
     "post": 1
   }
   ```

## Примеры запросов 2
- Получить список всех публикаций (GET): http://127.0.0.1:8000/api/v1/posts/

- Получение публикации по id (GET): http://127.0.0.1:8000/api/v1/posts/{id}/

- Получение комментария к публикации по id (GET): http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/

- Получение списка доступных сообществ (GET): http://127.0.0.1:8000/api/v1/groups/

- Добавление новой публикации в коллекцию публикаций (POST): (Анонимные запросы запрещены) http://127.0.0.1:8000/api/v1/posts/

- Обновление публикации (PUT): ( Обновить публикацию может только автор публикации. Анонимные запросы запрещены.) http://127.0.0.1:8000/api/v1/posts/{id}/

- Получить JWT-токен (POST): http://127.0.0.1:8000/api/v1/jwt/create/

## Ресурсы

```python
# Документаия проекта
http://127.0.0.1:8000/redoc/
```

```python
# ПО для тестирования API, Postman
https://www.postman.com/
```