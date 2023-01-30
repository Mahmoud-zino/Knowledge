## Motive
As the project needs a scheduling mechanism and we are using `Celerey` which needs a `rabbitmq` server to run.
Using the standard method is time consuming and it is hard to manage all servers separately.
Therefore we are using Docker.

## Docker

> Docker is a platform for building, shipping, and running distributed applications. It allows developers to package an application and its dependencies into a single container that can be easily moved between different environments and run consistently across different systems. This improves consistency, isolation, scalability, portability and cost-effectiveness.

## Commands

To run the compose with all containers
```bash
docker-compose up
```

> Note: make sure you are on the docker-compose.yml file level.

## Docker Components

### RabbitMQ

RabbitMQ is used for the communication between the celery worker and its beat.

> depends on -

### Django

Hosts our Application in `Alpine-linux` environment.

> depends on RabbitMQ

### Celery

Celery is used to run tasks periodically.

> depends on django  

## Diagram

![Docker stack](/images/docker.jpg)