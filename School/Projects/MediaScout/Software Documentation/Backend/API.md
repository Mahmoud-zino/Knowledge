**Table of content**
```toc
```
---
## Description

> An API (Application Programming Interface) is a set of rules and protocols that defines how two software systems can interact with each other. APIs allow different software systems to communicate with each other and exchange data in a structured and predictable way.

This page describes the Api used in the application

## API Interface

> API Path is built like the following:

```bash
<basePath>/api/<api_path>/<api_method>
Example: http://127.0.0.1:8000/api/user/get
```

### /admin

> the `admin` path is responsible for the admin dashboard.

### /auth

> The `auth` path is responsible for managing the program user.

|     API     |       PATH       | TYPE |       PARAMS       |    SUCCESS RETURN VALUE     | POSSIBLE STATUSES  | PERMISSION NEEDED |
|:-----------:|:----------------:|:----:|:------------------:|:---------------------------:|:------------------:|:-----------------:|
|    LOGIN    | /api/auth/login  | POST | username, password |  list of user permissions   | 200, 400, 401, 405 |         -         |
|   LOGOUT    | /api/auth/logout | GET  |         -          | "Message": "200 Logged out" |      200, 405      |         -         |
| PERMISSIONS |  /api/auth/perm  | GET  |         -          |  list of user permissions   |      200, 405      |         -         |

### /user

> the `user` path is responsible to manage the targeted user.

|  API   |       PATH       |  TYPE  |  PARAMS  |           SUCCESS RETURN VALUE           | POSSIBLE STATUSES  | PERMISSION NEEDED |
| :----: | :--------------: | :----: | :------: | :--------------------------------------: | :----------------: | :---------------: |
|  GET   |  /api/user/get   |  GET   |    -     |              all users data              |      200, 405      |         -         |
|  ADD   |  /api/user/add   |  POST  |   name   |            created user data             | 200, 400, 401, 405 |   api.add_user    |
|  EDIT  |  /api/user/edit  |  PUT   | id, name |             edited user data             | 200, 400, 401, 405 |  api.change_user  |
| DELETE | /api/user/delete | DELETE |    id    | "Message": "200 Deleted User with id: x" | 200, 400, 401, 405 |  api.delete_user  |

### /user/youtube

> the `youtube` path is responsible to manage the targeted user youtube record.

|  API   |                   PATH                    | TYPE |   PARAMS   |     SUCCESS RETURN VALUE      | POSSIBLE STATUSES  |  PERMISSION NEEDED  |
| :----: | :---------------------------------------: | :--: | :--------: | :---------------------------: | :----------------: | :-----------------: |
| CHECK  | /api/user/youtube/check/\<str:channel_id> | GET  |     -      |          channel id           |      200, 405      |          -          |
|  GET   |   /api/user/youtube/get/\<int:user_id>    | GET  |     -      | channel id and youtube obj id |   200, 400, 405    |          -          |
| MUTATE |  /api/user/youtube/mutate/\<int:user_id>  | POST | channel_id | channel id and youtube obj id | 200, 400, 401, 405 | api.add_youtubedata |

### /user/youtube/video

> the `video`path is responsible to manage the targeted youtube channel videos.

|     API      |                            PATH                             | TYPE | PARAMS |           SUCCESS RETURN VALUE           | POSSIBLE STATUSES | PERMISSION NEEDED |
| :----------: | :---------------------------------------------------------: | :--: | :----: | :--------------------------------------: | :---------------: | :---------------: |
|     GET      |       /api/user/youtube/get/\<int:youtube_id>/videos        | GET  |   -    | all videos of a youtube obj (only infos) |   200, 400, 405   |         -         |
|   DOWNLOAD   |      /api/user/youtube/videos/download/\<int:video_id>      | GET  |   -    |         downloads a single video         |   200, 400, 405   |         -         |
| DOWNLOAD_ALL | /api/user/youtube/get/\<int:youtube_id>/videos/download_all | GET  |   -    |  downloads all videos of a youtube obj   |   200, 400, 405   |         -         |