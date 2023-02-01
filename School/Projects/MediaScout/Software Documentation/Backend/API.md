**Table of content**
```toc
```
---

>[!info] Description
>An API (Application Programming Interface) is a set of rules and protocols that defines how two software systems can interact with each other. APIs allow different software systems to communicate with each other and exchange data in a structured and predictable way.

This page describes the Api used in the application

<div style="page-break-after: always;"></div>

## API Interface

API Path is built like the following:

```bash
<basePath>/api/<api_path>/<api_method>
Example: http://127.0.0.1:8000/api/user/get
```

### /admin

>[!tip] 
>The `admin` path is responsible for the admin dashboard.

### /auth

>[!tip] 
>The `auth` path is responsible for managing the program user.

|       PATH       | TYPE |       PARAMS       | POSSIBLE STATUSES  | PERMISSION NEEDED |
|:----------------:|:----:|:------------------:|:------------------:|:-----------------:|
| /api/auth/login  | POST | username, password | 200, 400, 401, 405 |         -         |
| /api/auth/logout | GET  |         -          |      200, 405      |         -         |
|  /api/auth/perm  | GET  |         -          |      200, 405      |         -         |

### /user

>[!tip] 
>the `user` path is responsible to manage the targeted user.

|       PATH       |  TYPE  |  PARAMS  | POSSIBLE STATUSES  | PERMISSION NEEDED |
|:----------------:|:------:|:--------:|:------------------:|:-----------------:|
|  /api/user/get   |  GET   |    -     |      200, 405      |         -         |
|  /api/user/add   |  POST  |   name   | 200, 400, 401, 405 |   api.add_user    |
|  /api/user/edit  |  PUT   | id, name | 200, 400, 401, 405 |  api.change_user  |
| /api/user/delete | DELETE |    id    | 200, 400, 401, 405 |  api.delete_user  |

<div style="page-break-after: always;"></div>

### /user/youtube

>[!tip] 
>The `youtube` path is responsible to manage the targeted user YouTube record.

|                   PATH                    | TYPE |   PARAMS   | POSSIBLE STATUSES  |  PERMISSION NEEDED  |
|:-----------------------------------------:|:----:|:----------:|:------------------:|:-------------------:|
| /api/user/youtube/check/\<str:channel_id> | GET  |     -      |      200, 405      |          -          |
|   /api/user/youtube/get/\<int:user_id>    | GET  |     -      |   200, 400, 405    |          -          |
|  /api/user/youtube/mutate/\<int:user_id>  | POST | channel_id | 200, 400, 401, 405 | api.add_youtubedata |

### /user/youtube/video

>[!tip] 
>The `video`path is responsible to manage the targeted YouTube channel videos.

|                            PATH                             | TYPE | PARAMS | POSSIBLE STATUSES | PERMISSION NEEDED |
|:-----------------------------------------------------------:|:----:|:------:|:-----------------:|:-----------------:|
|       /api/user/youtube/get/\<int:youtube_id>/videos        | GET  |   -    |   200, 400, 405   |         -         |
|      /api/user/youtube/videos/download/\<int:video_id>      | GET  |   -    |   200, 400, 405   |         -         |
| /api/user/youtube/get/\<int:youtube_id>/videos/download_all | GET  |   -    |   200, 400, 405   |         -         |

<div style="page-break-after: always;"></div>
