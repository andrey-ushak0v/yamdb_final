## Проект yamdb_final

![example workflow](https://github.com/andrey-ushakOv/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Описание проекта:

С помощью данного проекта можно развернуть образ приложения api_yamdb (проект по сбору отзывов о музыкальных произведениях) на своём сервере. Принцип подключения следующий:

1 С помощью настроек файла "yamdb_workflow.yml" происходит подключение к проекту на  GitHub, GitHub Actions производит автоматическую проверку кода линтером flake8, запуск тестов, а также сборку docker-образа и деплой проекта. При успешном выполнении всех шагов, на телеграм-бот приходит соответствующее сообщение;

2 Сборка docker-образа происходит на основании файлов Dockerfile и docker-compose.yaml, где находятся соответствующие инструкции. Образ собирается сервисе DockerHub, создаются 3 контейнера: web, db и nginx;

3 Проект запускается из сервиса DockerHub, после успешного запуска всех 3-х контейнеров.
Проект доступен по ссылке - http://51.250.97.250/redoc

# Подготовка и запуск проекта:

Клонировать репозиторий:

```git clone https://github.com/andrey-ushak0v/yamdb_final.git```

Запустить docker-compose:

```docker-compose up -d --build```

Выполнить миграции, создать суперпользователя, собрать статику.

```docker-compose exec web python manage.py migrate```

```docker-compose exec web python manage.py createsuperuser```

```docker-compose exec web python manage.py collectstatic --no-input``` 

Создать файл .env из директории infra/ и внестите в него данные:

```DB_ENGINE=django.db.backends.postgresql```

```DB_NAME=postgres```

```POSTGRES_USER=postgres```

```POSTGRES_PASSWORD= # установите свой пароль```

```DB_HOST=db```

```DB_PORT=5432```

# Автор: 

Ушаков Андрей - https://github.com/andrey-ushakOv
