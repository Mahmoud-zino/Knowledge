## Desired features
1. Archive youtube videos of registered channels.
2. Users can then download the videos using a website designated for this porpus.
3. Downloaded videos should be zipped so they won't take a lot of space.
## Team
Ralph Kartneller: Project manager
Simon Masooglu: Programmer
Mahmoud Zino: Programmer
## Architecture Design
![Project Architecture](images/projectArchitecture.png)
## Process description
1. The user visits our website.
2. The server response with the frontend view through the rest REST API.
3. The User registers a new youtube user through the UI.
4. The frontend page sends a request to the server using REST API.
5. The server requests the youtube user data from youtube API and Pytube.
6. The cellery beat (broker) requests to download all new videos every 60 seconds.
7. The cellery background worker