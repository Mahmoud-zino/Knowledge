## Installation steps
1. Runing `npm run build` on the front end will compile all frontend components, create a html template and replace the old one in django app.
2. Running docker compose using `docker-compose up` will build and run the container hosting the website to http://localhost:8000

> Note: To host the app publicly, a web server (like `Apache` or `Nginx`) will be needed.

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


## Important urls
1. Base Url: http://localhost:8000
2. API Url: http://localhost:8000/api
3. Rabbitmq Dashboard Url: http://localhost:15672

## Required Hardware
1. Any pc (windows or linux).
2. Internet Access (downloading videos from youtube requires internet access*)
3. enough space for all the downloaded youtube videos.

## Required Software
1. Docker engine (to run docker container)

## Operating system
The docker container can run on Windows or Linux.
It will download and setup an `python-alpine-linux` operating system for hosting the app.
### Linux
linux was chosen as an operating system, because it is developer friendly operating system and rabbitmq works only on linux.
### Alpine
Alpine was chosen because it is very lightweight and easy to work with.