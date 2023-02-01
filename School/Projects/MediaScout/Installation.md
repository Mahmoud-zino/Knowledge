## Installation steps
1. Running `npm run build` on the front end will compile all frontend components, create a HTML template and replace the old one in Django app.
2. Running docker compose using `docker-compose up` will build and run the container hosting the website to http://localhost:8000

> [!info] Note
> To host the app publicly, a web server (like `Apache` or `Nginx`) will be needed.

## Deinstallation steps
1. Delete the container using 
   ```bash
   docker container rm <ContainerName>
   ```
2. Delete the Image using
	```bash
	docker image rm <ImageName>
	```
1. Delete the volume using
	```bash
	doceker volume rm <VolumeName>
	```


## Important URLs
1. Base URL: http://localhost:8000
2. API URL: http://localhost:8000/api
3. RabbitMQ Dashboard URL: http://localhost:15672

## Required Hardware
1. Any pc (windows or Linux).
2. Internet access (downloading videos from YouTube requires internet access*)
3. enough space for all the downloaded YouTube videos.

## Required Software
1. Docker engine (to run docker container)

## Operating system
The docker container can run on Windows or Linux.
It will download and set up an `python-alpine-linux` operating system for hosting the app.
### Linux
linux was chosen as an operating system, because it is developer friendly operating system and RabbitMQ works only on Linux.
### Alpine
Alpine was chosen because it is very lightweight and easy to work with.


<div style="page-break-after: always;"></div>
