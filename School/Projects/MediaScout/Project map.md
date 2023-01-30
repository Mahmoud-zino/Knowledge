## Desired features
1.  [x] Archive YouTube videos of registered channels.
2. [x] Users can then download the videos using a website designated for this purpose.
3. [x] Downloaded videos should be zipped, so they won't take a lot of space.
4. [ ] Archive Twitter tweets (Optional)
## Team
Ralph Kartneller: Project manager
Simon Masooglu: Programmer
Mahmoud Zino: Programmer
## Architecture Design
![Project Architecture](images/projectArchitecture.png)
## Technologies
1. Svelte (Frontend)
2. REST API (API)
3. Django (Backend)
4. SQLite (Database)
5. RabbitMQ (Message queuing server)
## Process description
1. The user visits our website.
2. The server response with the frontend view through the rest API.
3. The User registers a new YouTube user through the UI.
4. The frontend page sends a request to the server using REST API.
5. The server requests the YouTube user data from YouTube API and Pytube.
6. The celery beat (broker) requests to download all new videos every 60 seconds.
7. The celery background worker will run to download the videos.
8. The user requests to download the video through REST API.
9. The server returns the video as a response to the REST API request.
## User Interface

## Timeline
![Timeline](images/timeline.png)
## Tasks distribution
### Backend
| Programmer      | Task                            |
| --------------- | ------------------------------- |
| Mahmoud Zino    | Django Project Setup            |
| Mahmoud Zino    | Create Database SQLite          |
| Mahmoud Zino    | Design Database models          |
| Mahmoud Zino    | Design Rest Interfaces          |
| Simon Masooglue | Download Videos                 |
| Simon Masooglue | Implement Zipping functionality |
| Mahmoud Zino    | Implement Tasks scheduling      |

### Containers
| Programmer   | Task                      |
| ------------ | ------------------------- |
| Mahmoud Zino | Create Celery Container   |
| Mahmoud Zino | Create Django Container   |
| Mahmoud Zino | Create Rabbitmq Container |

### Frontend
| Programmer      | Task                          |
| --------------- | ----------------------------- |
| Mahmoud Zino    | Svelte Project Setup          |
| Mahmoud Zino    | Configur eslint & prettier    |
| Simon Masooglu  | Setup App Theme               |
| Simon Masooglu  | Create UI Elements            |
| Simon Masooglu  | Create Axios API Manager      |
| Simon Masooglu  | Create Login Logic            |
| Simon Masooglu  | Create Users Management Logic |
| Simon Masooglue | Mutate Youtube Channel Logic  |
| Simon Masooglue | Download Youtube videos       | 

## Problems
### YouTube API

> [!bug] Desciption
> The youtube data api has a very limited amount of usable interfaces when it comes to getting a channeld id.

> [!done] Solution
> 