## AuthUser

>[!info] 
>The AuthUser class represents a logged-in user.

|  Property   |   Type   | Description |
|:-----------:|:--------:|:----------:|
|    name     | string  \| undefined  | Username of the logged-in user. |
| permissions | string[] \| undefined  | List of permissions user has.    |

<div style="page-break-after: always;"></div>

## User

>[!info] 
>The User class represents a created user.

|  Property   |   Type   | Description |
|:-----------:|:--------:|:----------:|
|    id     | number  \| undefined  | Identifier for the user. |
|    name     | string  \| undefined  | Name of the created user. |
| youtube | YoutubeData \| undefined  | YouTube object which has all YouTube data of the user.    |

## YoutubeData

>[!info] 
>The #YoutubeData class represents the YouTube information for one user.

|  Property   |   Type   | Description |
|:-----------:|:--------:|:----------:|
|    id     | number  \| undefined  | Identifier for YouTube data. |
|    channel_id     | string  \| undefined  | ID of the YouTube channel. |
| videos | YoutubeVideo[] \| undefined  | Array of YoutubeVideo objects which represent a video.    |

## YoutubeVideo

>[!info] 
>The YoutubeVideo class represents the one YouTube video.

|  Property   |   Type   | Description |
|:-----------:|:--------:|:----------:|
|    id     | number  \| undefined  | Identifier for YouTube video. |
|    video_id     | string  \| undefined  | ID of the YouTube video. |
| title | string \| undefined  | Title of the YouTube video.    |
| length | number \| undefined  | Length of the YouTube video in seconds.    |
| published_at | date \| undefined  | Date when the video was published.    |

<div style="page-break-after: always;"></div>
