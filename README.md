# yamdb_final
***Проект YaMDb***

Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен администратором (например, можно добавить категорию «Картины» или «Ювелирка»).

Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

Как запустить проект YaMDb:

*** Установка и запуск: ***

- Клонировать репозиторий и перейти в него в командной строке (используем ssh):

`git clone git@github.com:YaroslavAndreev/yamdb_final.git
`
- Добавьте файл .env в котором хранится SECRET_KEY и настройки БД:

`cd yamdb_final/infra
`

```
echo "SECRET_KEY=YourSecretKey 
DB_ENGINE=django.db.backends.postgresql 
DB_NAME=postgres 
POSTGRES_USER=postgres 
POSTGRES_PASSWORD=postgres 
DB_HOST=db DB_PORT=5432" > .env
```
- Пример заполнения файла .env: 

```
SECRET_KEY='secretkey'
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql 
DB_NAME=postgres # имя базы данных 
POSTGRES_USER=postgres # логин для подключения к базе данных 
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой) 
DB_HOST=db # название сервиса (контейнера) 
DB_PORT=5432 # порт для подключения к БД 
```

- Cборка docker-compose:

`sudo docker-compose up
` 

`sudo docker-compose exec python manage.py makemigrations
`

`sudo docker-compose exec python manage.py migrate
`

`sudo docker-compose exec python manage.py createsuperuser
`

`sudo docker-compose exec python manage.py collectstatic
`

- Заполнение базы данными:

`sudo docker-compose exec python manage.py load_info
`

- Получаем ключ авторизации для получения токена:

`sudo docker-compose exec web bash
`

Документация по проекту Yamdb_final: http://84.252.139.137:8000/redoc/

![example workflow](https://github.com/YaroslavAndreev/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

Разработчик: Андреев Ярослав.