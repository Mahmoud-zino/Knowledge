## Project Map
```toc
max_depth: 3
```

<div style="page-break-after: always;"></div>

## Desired features
1.  [x] Archive YouTube videos of registered channels.
2.  [x] Users can then download the videos using a website designated for this purpose.
3.  [x] Downloaded videos should be zipped, so they won't take a lot of space.
4.  [ ] Archive Twitter tweets (Optional)

## Team
Ralph Kartneller: Project manager
Simon Masooglu: Programmer
Mahmoud Zino: Programmer
## Architecture Design
![Project Architecture](images/projectArchitecture.png)

<div style="page-break-after: always;"></div>

## Technologies
>[!abstract] Svelte (Frontend)
> Svelte is a fast / easy to use frontend framework.

>[!abstract] REST API (API)
> REST API is the standard secured bridge between Backend and Frontend.

>[!abstract] Django (Backend)
> Using python as our Backend makes web scraping and task managing easy.
> In addition, Django comes with an out-of-the-box admin dashboard which we needed.

>[!abstract] SQLite (Database)
>SQLite is just like any other database, but very lightweight and already setup with Django.

>[!abstract] RabbitMQ (Message queuing server)
> RabbitMQ is one of the easy-to-use message queuing servers, and it comes with an out-of-the-box dashboard to manage and debug it.
> >[!warning]
> >RabbitMQ requires a Linux server to run.

>[!abstract] Docker (Containers)
>As stated above, RabbitMQ requires a Linux server and the only way to achieve that on our Windows pc's is using containers.
>> [!done] 
>> Docker removes the need to configure the server every time.

<div style="page-break-after: always;"></div>

## Process description
1. The user visits our website.
2. The server responds with the frontend view through the rest API.
3. The User registers a new YouTube user through the UI.
4. The frontend page sends a request to the server using REST API.
5. The server requests the YouTube user data from YouTube API and Pytube.
6. The celery beat (broker) requests to download all new videos every 60 seconds.
7. The celery background worker will run to download the videos.
8. The user requests to download the video through REST API.
9. The server returns the video as a response to the REST API request.

## Timeline
![Timeline](images/timeline.png)

<div style="page-break-after: always;"></div>

## User Interface
### Sidebar

![Side Bar](images/sideBar.png)

1. #Login Click to open the login modal.
2. #Search Search through the names of the users in the list below.
3. #UserList List of users. Click to select user.
   
### Login

![login](images/login.png)

1. #Username Enter username to login.
2. #Password Enter password of the user to login.

<div style="page-break-after: always;"></div>

#### When logged in

![logged in](images/loggedIn.png)

1. #LogOut Click to log out.
2. #AddUser Click to open the add user modal.

### Add user

![logged in](images/addUser.png)
1. #ProfileName Enter a name for the new user.

<div style="page-break-after: always;"></div>

### Main view

![Main View](images/mainView.png)

1. #EditUser Click to open the edit user modal.
2. #ChannelID Enter a valid channel ID to fetch data from.
3. #Download Click to download all videos of this user.
4. #Information Shows if the current channel ID is valid to fetch data from.
5. #Search Search through the video titles of the videos in the list below.
6. #VideoList List of videos from the selected channel.
7. #Download Click to download the video of that row.

### Edit user

![Main View](images/editUser.png)

1. #EditUser Edit the name of the user.
2. #Delete Click to delete the user including all its data.

<div style="page-break-after: always;"></div>

## Tasks distribution
### Backend
| Programmer      | Task                                      |
| --------------- | ----------------------------------------- |
| Mahmoud Zino    | Django Project Setup                      |
| Mahmoud Zino    | Create Database SQLite                    |
| Mahmoud Zino    | Design Database models                    |
| Mahmoud Zino    | Design Rest Interfaces                    |
| Simon Masooglu | Download Videos                           |
| Simon Masooglu | Implement Zipping functionality           |
| Mahmoud Zino    | Implement Tasks scheduling                |
| Mahmoud Zino    | Automatically compile and deploy frontend |

### Containers
| Programmer   | Task                      |
| ------------ | ------------------------- |
| Mahmoud Zino | Create Celery Container   |
| Mahmoud Zino | Create Django Container   |
| Mahmoud Zino | Create RabbitMQ Container |

### Frontend
| Programmer      | Task                          |
| --------------- | ----------------------------- |
| Mahmoud Zino    | Svelte Project Setup          |
| Mahmoud Zino    | Configure ESLint & prettier    |
| Simon Masooglu  | Create UI Elements            |
| Simon Masooglu  | Create Axios API Manager      |
| Simon Masooglu  | Create Login Logic            |
| Simon Masooglu  | Create Users Management Logic |
| Simon Masooglu | Mutate YouTube Channel Logic  |
| Simon Masooglu | Download YouTube videos       | 

<div style="page-break-after: always;"></div>

## Problems
### YouTube API

> [!bug] Description
> The YouTube data API has a very limited amount of usable interfaces when it comes to getting a channel ID.

> [!fail] failed attempts
>> [!help] API
>> We tried to use the YouTube API to get the channel ID, but there was not an option which would consistently return the correct ID.
>
>> [!help] Script files
>> The channel_id can also be found in the script of the YouTube channel page. But we couldn't retrieve it.
>
>> [!help] JS loaded html
>> If you wait for the JS to load additional meta tags into the page, you can retrieve the channel ID out of it. The problem is that using a library like selenium takes a long time to load, and you can not get past the YouTube consent dialog, which blocks you from entering the HTML of the website.

> [!done] Solution
> Unfortunately, there is no consistent way of getting the channel ID via a channel link. Therefor, we required the user to input the channel ID himself.

<div style="page-break-after: always;"></div>

### Task scheduling

> [!bug] Description
> Celery needs a RabbitMQ server which is not compatible with windows.

> [!fail] Failed attempts
>> [!help] Synchronous tasks
>> When using synchronous task we don't need a RabbitMQ server but the task blocks the main thread causing the server to:
>> "hang hang hang hang" - Takashi 69 
>
>> [!help] RabbitMQ with local Linux server
>> Setting RabbitMQ up with a local Linux server works, but introduces a lot of setup time.

> [!done] Solution
> With docker, we created a container for every service needed, cutting the setup time to zero.

<div style="page-break-after: always;"></div>

## Conclusion
The project Media Scout was a very interesting project for us. 
We learned a lot with the new technologies we used. 
Django, an easy-to-use python backend framework with an out-of-the-box admin dashboard. 
Svelte a fast JS framework that makes creating UI a fun experience. 
Docker, where we deepened our knowledge about containers and the possibilities containerizing services comes with. 
Scheduling tasks with RabbitMQ and managing them with celery gave us the opportunity to learn about queuing messages and how they interact with background workers.

We also learned a lot about project management and task distribution among a team of developers.
It was a very good idea to plan only the base function of the project and set some pivot time to solve problems that we could face.
As we experienced, we faced a lot of unplanned problems and because of the pivot planning we had enough time to react and resolve these problems.
On the other side we had also some optional features planned but as expected the time was tight, and we had to skip those.

| Goal                                                                          | Current                                                                                                                  |
|:----------------------------------------------------------------------------- |:------------------------------------------------------------------------------------------------------------------------ |
| define user permissions                                                       | every user has his own permissions                                                                                       |
| manage user permission                                                        | an admin can manage user permissions using the admin dashboard                                                           |
| login                                                                         | User can log in to the website using his credentials                                                                     |
| display list of registered users                                              | In the side menu there is a list of searchable registered users with avatars                                             |
| selecting a user display his social media posts                               | selecting a user will open a view on the main page with the user social media posts                                      |
| Register a new social media user when the user has the required permissions   | Users with the Permission (add-user) will see an add button which opens a modal to add a new social media user           | 
| Edit an existing social media user when the user has the required permissions | Users with the Permission (edit-user) will see an edit button which opens a modal to edit the existing social media user |
| Fetch new YouTube videos every 60 seconds                                     | Download videos every 60 seconds using tasks                                                                             |
| User can Download all videos of a social media user                           | Download button beside the username will download all his videos                                                         |
| User can Download a specific video of a social media user                     | Download button beside the video will download only the selected video                                                   |

##### Completed goals
At the end, we managed to complete our original goal of creating a clean and easy to use frontend to manage users and download posts. 
We build a backend which fetches new YouTube videos of the users every minute and schedules them to download in the background. 
Every video the users have ever uploaded to YouTube are saved on the server and can be downloaded from it anytime anywhere.


---
<div style="display: flex; justify-content: space-between">
<span>Mahmoud Zino</span>
<span>Simon Masooglu</span>
</div>
<br>
<div>4APEC</div>
<div>©MediaScout</div>

