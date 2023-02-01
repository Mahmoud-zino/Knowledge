## Motive
As the project needs a scheduling mechanism, and we are using `Celerey` which needs a `rabbitmq` server to run.
Using the standard method is time-consuming and it is hard to manage all servers separately.
Therefore, we are using Docker.

## Docker

>[!info] Description 
>Docker is a platform for building, shipping, and running distributed applications. It allows developers to package an application and its dependencies into a single container that can be easily moved between different environments and run consistently across different systems. This improves consistency, isolation, scalability, portability and cost-effectiveness.

## Commands

To run the compose command with all containers
```bash
docker-compose up
```

>[!note] 
>make sure you are on the docker-compose.yml file level.

<div style="page-break-after: always;"></div>

## Docker Components

### RabbitMQ

RabbitMQ is used for the communication between the celery worker and its beat.

>[!danger] Depends on
> -- 

### Django

Hosts our Application in `Alpine-linux` environment.

>[!danger] Depends on
> RabbitMQ

### Celery

Celery is used to run tasks periodically.

>[!danger] Depends on
> Django  

## Diagram

![Docker stack | 300](/images/docker.jpg)
