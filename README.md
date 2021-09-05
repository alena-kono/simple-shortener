Simple Shortener
================

![image](https://img.shields.io/badge/built%20with-Cookiecutter%20Django-ff69b4.svg?logo=cookiecutter%0A%20%20:target:%20https://github.com/pydanny/cookiecutter-django/%0A%20%20:alt:%20Built%20with%20Cookiecutter%20Django)

Работает на Python 3.9.x и Django 3.1.13.

Цели проекта
------------

Данный проект выполнялся в рамках тестового задания.
Формулировка задания:

*Наша компания отправляет СМС с трекинговой ссылкой, но ссылка достаточно длинная и из-за этого СМС выходит за 70 символов (длина 1 СМС).Необходимо спроектировать сервис-укорачиватель ссылок, чтобы сэкономить деньги компании.*

Ключевые моменты разработки проекта
-----------------------------------

1. Структура приложения - микросервис. Короткую ссылку можно получить GET запросом из другого сервиса.
2. Основной инструмент - фреймворк Django.
Django выбран в качестве рабочего фреймворка в целях демонстрации потенциальному работодателю своих навыков разработки на Django.
Под указанную структуру приложения лучше подошли бы Flask, Django Rest Framework.
3. Структура данных и хранилище.
Выбрана реляционная СУБД (конкретно - PostgreSQL), так как предполагается, что структура данных будет однородна, а, значит, схема данных может быть заранее определена и жестко зафиксирована.
4.

Telegram bot is deployed at production. Link is
[here](https://t.me/valley_test_task_bot).

Link to the Django admin panel is
[here](https://alena-kono.space/zrhsMcJeJNXUnXuKKPCSSoAFkxLm2DcS/dynamic_preferences/globalpreferencemodel/).

Test task checklist
-------------------

✅ Telegram bot

- ✅ Production - webhook, development - long polling
- ✅ /start command
- ✅ ReplyKeyboardMarkup with 3 buttons - BTC, ETH, DOGE
- ✅ Getting current exchange rate (to USD) when push the corresponding button
- ✅ Error messages
- ✅ Cryptocurrency API integration (CryptoCompare as a provider)

✅ Django admin panel

- ✅ List of telegram bot users (fields - First launch of the
    bot, User ID, @Username, Last Name)
- ✅ Configured search bar and filters
- ✅ Editable bot messages and buttons
    (django-dynamic-preferences)
- ✅ No unnecessary links, buttons, sections, etc.
- ✅ Custom styles (CSS)

Further plans
-------------
⬜️ Validation at admin panel preferences

⬜️ Tests

⬜️ Mypy successful checks

Settings
--------

To run your project for both development and production you should have
the following files that contain all the settings:

    $ cd .envs

    $ tree -a

      $ ├── .local
      $ │   ├── .django
      $ │   ├── .postgres
      $ │   └── .telegram
      $ └── .production
      $     ├── .django
      $     ├── .postgres
      $     └── .telegram

Installation and running locally (development)
----------------------------------------------

1.  Check whether PostgreSQL, Docker, Docker-compose, Git are installed
    and set up on your machine.

2.  Within your virtual env:

        $ pip install -r requirements/local.txt

3.  Run migrations within docker container:

        $ docker-compose -f local.yml run --rm django python manage.py migrate

4.  Create superuser to get an access to the admin panel:

        $ docker-compose -f local.yml run --rm django python manage.py createsuperuser

5.  Build and up this project using docker-compose:

        $ docker-compose -f local.yml up --build -d

Installation and running globally (production)
----------------------------------------------

1.  Check whether PostgreSQL, Docker, Docker-compose, Git are installed
    and set up on your machine.

2.  Run migrations within docker container:

        $ docker-compose -f production.yml run --rm django python manage.py migrate

3.  Create superuser to get an access to the admin panel:

        $ docker-compose -f production.yml run --rm django python manage.py createsuperuser

4.  Build and up this project using docker-compose:

        $ docker-compose -f production.yml up --build -d
