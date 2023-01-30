## Possible errors
### Server has no Internet connection
Adding a new channel when the server has no internet connection will be displayed on the UI, as the channel ID is not fetchable.
### Server unstable internet connection
If the connection with the internet is lost while downloading a video, the video is displayed as downloaded in the database and the download will never be restarted, causing a corrupted video file.
### Duplicated User with the same Channel ID
When adding a duplicated User with the same channel ID, the new user is saved to the database, but the videos are not retrieved again because they are unique in the database.
On the UI, the duplicated user is displayed with empty page.
## Logging
1. Backend: Every action is logged right now to the `Console` using the Django logging module.
2. Frontend: No logs are used at the moment.
3. Celery: Every action is logged to the `Console` also using the Django logging module.
## Configuration
### Backend Configs
#### env file
in the .env file, the following configurations are saved:
1. API_KEY: application YouTube API key. Retrieved from https://console.cloud.google.com/apis/dashboard
2. QUOTA_USER: just a unique name to access the YouTube API.
3. DATA_PATH: where the downloaded videos are saved in the Django API app Folder.
#### Settings.py
Contains a lot of the Django project Configurations like:
1. Project build path
2. allowed hosts
3. Installed apps
4. Middlewares
5. CORS configs
6. Templates
7. Database
8. Password Validators
9. Languages & Timezones
10. URLs
### Frontend
in the .env file all `API`, `Permissions` and `URLS` ares saved to be used in the frontend svelte application.
## Implementation decisions
### Celery Asynchronous Tasks
Downloading the videos Synchronously will block the main thread of the server, causing it to hang and not response to other API requests.
Therefore, Celery was used to take full advantage of the asynchronous workers.
## Third party Software
### YouTube API
> The YouTube API is an API developed by Google that allows developers to access and interact with YouTube content and functionality.

It is used to check if a channel ID is correct and to retrieve YouTube videos Ids from the channel.
> Note: We can't download videos using the YouTube API.

### Pytube
> is a Python library that allows you to download YouTube videos and extract information about them. It provides a simple and easy-to-use interface for downloading YouTube videos, as well as for accessing various video details such as title, description, and thumbnail.

It is used to get videos information and download the videos.

