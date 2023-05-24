![example workflow](https://github.com/Sarugot/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# Проект YaMDb API
## Авторы:

[anthony-bogi](https://github.com/anthony-bogi)

[torgov1](https://github.com/torgov1)

[Sarugot](https://github.com/Sarugot)


## Описание:
### Проект YaMDb API

Проект YaMDb собирает отзывы пользователей на различные произведения.


## Технологии

Python 3.7

Django 3.2

Docker 3.8


## Шаблон наполнения env-файла:

```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```


## Описание команд для запуска приложения в контейнерах:

Перейти в папку с файлом docker-compose:

```
cd infra
```

Запустить контейнеры:

```
docker-compose up -d --build
```

Выполнить миграции:

```
docker-compose exec web python manage.py migrate
```

Создать суперпользователя:

```
docker-compose exec web python manage.py createsuperuser
```

Собрать статику:

```
docker-compose exec web python manage.py collectstatic --no-input
```

Загрузить базу данных:

```
docker cp fixtures.json <id>:app/
docker-compose exec web python manage.py loaddata fixtures.json
```