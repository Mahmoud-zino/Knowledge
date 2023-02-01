>[!info] Description
>A store in Svelte is a global state management tool that allows you to share data between components in your Svelte application. A store is similar to a reactive variable, but it is designed to be shared and accessed from multiple components. The value of a store can be updated from any component, and changes to the store are automatically propagated throughout the application.
## AlertStore

The AlertStore is shared on the entire application for warnings/errors to be shown.

|  Field   |   Type   | Description |
|:-----------:|:--------:|:----------:|
|    message     | string \| null  | Message to display on the page. |

```js
// Show alert with message
showAlert.set(`Message to show!`)
// Clear alert
showAlert.set(null)
```

<div style="page-break-after: always;"></div>
