## ApiManager

>The ApiManager is used to wrap the axios library for easier use.

```js
// Call API. + method
API.post(
	// Pass in path and parameters
)
  .then(res => {
	// Get result when finished
  })
  .catch(err => {
	// Catch errors
  })
```

## ValidationManager

>The ValidationManager is used to validate user input.

### Functions

| Name   |      Parameter      |  Desciption |
|:--------:|:-------------:|:-----:|
| isValidYouTubeChannelId |  id: string | Checks if the id is a valid youtube channel id for #YoutubeData Model |
