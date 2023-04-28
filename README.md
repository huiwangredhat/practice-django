## Project:
This is a practice project for learning django.
The project name is mysite.
```shell
$ tree mysite/
mysite/ # root directory is a container for your project
├── manage.py # A command-line utility
├── mysite # directory is the actual Python package for your project
│   ├── asgi.py
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── README.md
```

## Start server:
```shell
$ python manage.py runserver 0:8000
```

## APP:
The app name is polls.
```shell
$ tree polls/
polls/
├── admin.py
├── apps.py
├── __init__.py
├── migrations
│   └── __init__.py
├── models.py
├── tests.py
└── views.py
```

## The references:
```text
https://docs.djangoproject.com/en/4.2/
https://docs.djangoproject.com/zh-hans/4.2/
```
