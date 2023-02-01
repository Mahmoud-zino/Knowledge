## ApiManager

>[!info] 
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

>[!info] 
>The ValidationManager is used to validate user input.

### Functions

| Name   |      Parameter      |  Description |
|:--------:|:-------------:|:-----:|
| isValidYouTubeChannelId |  id: string | Checks if the ID is a valid YouTube channel ID for #YoutubeData Model |
