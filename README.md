# api_final

## Автор:
Марк Порошин (https://github.com/Markporsh) 


## Описание:
api final - это REST API для блог-платформы Yatube. Позволяет просматривать и отправлять посты, просматривать группы, подписываться на авторов.

## Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке:
```
git clone https://github.com/Markporsh/api_final_yatube
```
```
cd api_final_yatube
```
Cоздать и активировать виртуальное окружение:
```
python -m venv venv
```
```
source venv/Scripts/activate 
```
Установить зависимости:
```
python -m pip install --upgrade pip
```
```
pip install -r requirements.txt
```
Выполнить миграции:
```
python manage.py migrate
```
Запустить проект:
```
python manage.py runserver
```
## Примеры запросов:
### Запрос JWT токена с использованием логина и пароля пользователя Mark:
```
  [POST].../api/v1/jwt/create/
  {
    "username": "Mark",
    "password": "1234567bb"
}
```
### Ответ:
```
{"refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTY1MjA5NTYwNywianRpIjoiMDBmMGI0MG.sE5Bd3vrnQLIAL5GxxFg36tPoYyB9I5MQBE_iGshpK4",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjUyMDk1NjA3LCJqdGkiOiI0YmIxN2MzODcwNGU0YzQ0OWQ4Nzg4NzA4ODcyZTliMCIsInVzZXJfaWQiOjF9"
}
```
### Запрос с использованием токена пользователя Mark для публикации поста:
```
    [POST].../api/v1/posts/
    {
    "text": "Привет",
    "group": 1   
    }
```
### Ответ:
```
{
    "id": 2,
    "text": "Привет",
    "author": "Mark",
    "image": null,
    "group": 1,
    "pub_date": "2022-05-08T11:48:48.782688Z"
}
```
### Запрос для просмотра групп анонимным пользователем:
```
    [GET].../api/v1/groups/
```
### Пример ответа:
```
    [
    {
        "id": 1,
        "title": "Группа для всех",
        "slug": "foreveryone",
        "description": ""
    },
    {
        "id": 2,
        "title": "Котолюбители",
        "slug": "catslovers",
        "description": "Мур"
    }
]
