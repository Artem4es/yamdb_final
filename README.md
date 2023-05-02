### Что это за проект?:smiley_cat:
Всё просто: YaMDb - это бэкенд для сбора отзывов и оценок о произведениях (книги, фильмы, музыка) + API реализованный на Django Rest Framework.
Он предоставляет интерфейс для удобного взаимодействия с бизнес-логикой сервиса в формате JSON.

### Как запустить? :space_invader:
Проект можно запустить, используя Docker для этого:

Клонировать репозиторий:

```
git clone git@github.com:Artem4es/yamdb_final.git
```
Перейти в папку /infra

```
cd yamdb_final/infra
```

Запустить контейнеры:

```
docker compose up -d --build
```

Для полноценного функционирования проекта необходимо выполнить миграции и собрать статику:
- Зайти в контейнер web

```
docker exec -it <CONTAINER ID> bash
```

- Выполнить миграции и сollectstatic в папке с manage.py

```
python3 manage.py makemigrations
python3 manage.py migrate
python3 manage.py collectstatic
```


### Начало взаимодействия с API :old_key:
После запуска проекта, в версии V1 доступны для GET-запросов все [эндпоинты](http://127.0.0.1:8000/api/v1/) кроме списка пользователей http://127.0.0.1:8000/api/v1/users/. (Доступен только администратору)
Для получения полного доступа к интерфейсу необходимо: 

1. Зарегистровать нового пользователя, отправив POST запрос 
с именем пользователя и почтой в формате:

```
{
"email": "user@example.com",
"username": "string"
}
```
на адрес http://127.0.0.1:8000/api/v1/auth/signup/. В ответ на указанную почту придёт письмо с кодом активации.

2. Получить JWT-токен, отправив POST запрос в формате: 
```
{
"username": "string",
"confirmation_code": "string"
}
```
на эндпоинт http://127.0.0.1:8000/api/v1/auth/token/. В ответ придёт токен в формате JSON.
Токен из строки "token" необходимо отправлять в headers запроса с ключом Authorization. Значение ключа в виде Bearer "ваш токен без ковычек".
Срок действия токена - 24 часа. Необходимо обновление по истечении срока.

### Документация проекта: :blue_book:
После запуска проекта (python3 manage.py runserver) документация со списком эндпоинтов доступна по ссылке:
http://127.0.0.1:8000/redoc

![example workflow](https://github.com/artem4es/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
