**Table of Contents**
```toc
```
---
## Celery

> Celery is an open-source task queue or job queue written in Python that allows you to run asynchronous tasks in the background. It can be used to offload long-running tasks from a web application so that the web server can continue to handle new requests. Celery uses a message broker (such as RabbitMQ or Redis) to communicate between the web application and the task queue. This allows tasks to be added to the queue and executed by worker processes on separate machines, making it useful for distributed systems.

## Setup

```bash
pip install celery[rabbitmq]
```

Add `celery.py` to the root project.

```py
import os
from celery import Celery
from celery.schedules import crontab
from api.tasks import test_task

# load django default settings
os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'mediaScout_django.settings')

# add rabbitmq as broker
app = Celery('mediaScout_django', broker='amqp://guest:guest@rabbitmq:5672/')

app.config_from_object('django.conf:settings', namespace='CELERY')

# discover tasks with the tag @shared_task
app.autodiscover_tasks()

# configure tasks
@app.on_after_configure.connect
def setup_periodic_tasks(sender, **kwargs):
    sender.add_periodic_task(10.0, test_task, name='add every 10')
```

Add celery to `__init__.py`

```py
from .celery import app as celery_app

__all__ = ('celery_app',)
```

Tasks are then added in `tasks.py` in api app.

> example

```py
from celery import shared_task

@shared_task
def test_task ():
    print("nice task")
```

## Running the tasks

the tasks are then run from the docker container, with help of the following command:

```bash
celery -A mediaScout_django worker --beat --loglevel=info
```

> [!info] Note
> this command works only in linux environment for windows another command should be used.

## Available Tasks

### update_youtube_videos
Is executed every 60 seconds and searches all channels exiting in the data base and try to get a list of youtube videos that are not already installed.

### download_new_videos
Downloads a video when triggered.