## AuthUser

>The AuthUser class represents a logged in user.

|  Property   |   Type   | Desciption |
|:-----------:|:--------:|:----------:|
|    name     | string  \| undefined  | User name of the logged in user. |
| premissions | string[] \| undefined  | List of premissions user has.    |

## User

>The User class represents a created user.

|  Property   |   Type   | Desciption |
|:-----------:|:--------:|:----------:|
|    id     | number  \| undefined  | Identifier for the user. |
|    name     | string  \| undefined  | Name of the created user. |
| youtube | YoutubeData \| undefined  | Youtube object which has all youtube data of the user.    |

## YoutubeData

>The #YoutubeData class represents the youtube information for one user.

|  Property   |   Type   | Desciption |
|:-----------:|:--------:|:----------:|
|    id     | number  \| undefined  | Identifier for youtube data. |
|    channel_id     | string  \| undefined  | Id of the youtube channel. |
| videos | YoutubeVideo[] \| undefined  | Array of YoutubeVideo objects which represent a video.    |

## YoutubeVideo

>The YoutubeVideo class represents the one youtube video.

|  Property   |   Type   | Desciption |
|:-----------:|:--------:|:----------:|
|    id     | number  \| undefined  | Identifier for youtube video. |
|    video_id     | string  \| undefined  | Id of the youtube video. |
| title | string \| undefined  | Title of the youtube video.    |
| length | number \| undefined  | Length of the youtube video in seconds.    |
| published_at | date \| undefined  | Date when the video was published.    |
