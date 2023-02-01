**Table of Contents**

```toc

```
---
## Django setup

> Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.

> Used Python version: 3.11.0

### Install Django

```bash
python -m pip install Django
pip install djangorestframework
```
Verify installation
```bash
python -m django --version
```

### Initialize django project
```bash
django-admin startproject mediaScout_django
```
Verify Initialization
```bash
python manage.py runserver
```
Then visit the following address: http://127.0.0.1:8000 and you should see the following:
![django Startup](/images/djangoStartup.png)

## Create App

> An app is a web application that does something – e.g., a blog system, a database of public records or a small poll app.

```bash
python manage.py startapp api
```


### Register the app in the Project
Add the following in `settings.py`
```py
INSTALLED_APPS = [
    'api.apps.ApiConfig'
]
```

## Setup Django CORS

```
pip install django-cors-headers
```
Register Cors in `settings.py`

```py
INSTALLED_APPS = [
    'corsheaders',
]
```
Add Cors Middleware
```py
MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware',
]
CORS_ALLOW_CREDENTIALS = True
CORS_ALLOW_HEADERS = [
    'x-csrftoken',
    'content-type',
]
```

> [!info] Note
> CorsMiddleware should be placed as high as possible, especially before any middleware that can generate responses such as CommonMiddleware.

## Setup SQLite

> SQLite is a database engine. It is software that allows users to interact with a relational database. In SQLite, a database is stored in a single file.
  
### Installation
SQLite is already installed with django.

Database settings in `settings.py`

```py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

### Create Migration

To create a migration:
```bash
python manage.py migrate
```

## Django Admin

> Generating admin sites for your staff or clients to add, change, and delete content is tedious work that doesn’t require much creativity. For that reason, Django entirely automates creation of admin interfaces for models.

### Create super user

```bash
python manage.py createsuperuser
```

### Test super user

After running the server, visit /admin and login with the superuser credentials.

You should see something like this:

![django Admin page](/images/djangoAdminPage.png)

## Env Variables

> to load sensitive data from a file django uses python-dotenv package.

### Installation

```bash
pip install python-dotenv
```

### env file

Create an .env file in the project root and write all env Variables needed.

```env
API_KEY=XXXXXXXXXXXXXXXXXXXXXXX
```

### Usage

To use the variables then

```py
import os
from dotenv import load_dotenv

load_dotenv()

API_KEY = os.getenv('API_KEY')
```

> [!info] Note
> that `.env` file should be ignored in the `.gitignore` file so no keys are leaked to github.

## Youtube API

to interact with the youtube api use the package `google-api-python-client`.

```bash
pip install google-api-python-client
```