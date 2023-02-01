
## Django setup

>[!info] Description
>Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.

>[!info] Used Python version: 3.11.0

### Install Django

```bash
python -m pip install Django
pip install djangorestframework
```
Verify installation
```bash
python -m django --version
```

### Initialize Django project
```bash
django-admin startproject mediaScout_django
```
Verify Initialization
```bash
python manage.py runserver
```
Then visit the following address: http://127.0.0.1:8000 and you should see the following:
![django Startup | 350](/images/djangoStartup.png)

## Create App

>[!info] 
>An app is a web application that does something – e.g., a blog system, a database of public records or a small poll app.

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
Register CORS in `settings.py`

```py
INSTALLED_APPS = [
    'corsheaders',
]
```
Add CORS Middleware
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

> [!note] Note
> Cors Middleware should be placed as high as possible, especially before any middleware that can generate responses, such as Common Middleware.

<div style="page-break-after: always;"></div>

## Setup SQLite

>[!info] 
>SQLite is a database engine. It is software that allows users to interact with a relational database. In SQLite, a database is stored in a single file.
  
### Installation
SQLite is already installed with Django.

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

>[!info] 
>Generating admin sites for your staff or clients to add, change, and delete content is tedious work that doesn’t require much creativity. For that reason, Django entirely automates creation of admin interfaces for models.

### Create superuser

```bash
python manage.py createsuperuser
```

### Test superuser

After running the server, visit /admin and login with the superuser credentials.

You should see something like this:

![django Admin page | 350](/images/djangoAdminPage.png)

## Env Variables

>[!info] 
>To load sensitive data from a file, Django uses python-dotenv package.

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

```py
import os
from dotenv import load_dotenv

load_dotenv()

API_KEY = os.getenv('API_KEY')
```

> [!note] Note
> that `.env` file should be ignored in the `.gitignore` file, so no keys are leaked to GitHub.

## YouTube API

To interact with the YouTube API use the package `google-api-python-client`.

```bash
pip install google-api-python-client
```

<div style="page-break-after: always;"></div>
