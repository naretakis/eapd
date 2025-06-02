[[redux.png]]

[source](https://github.com/reduxjs/redux/issues/653)

## Redux

> Redux is a predictable state container for JavaScript apps. - [redux.js.org](https://redux.js.org/)

## Core Concepts

These are the core concepts of Redux.

* The `state` of your application is represented as an object within the **store**.
* `state` is read-only.
* Changes to the application state are made via "pure" functions (aka - **reducers**).

Describe your application's `state` in the form of arrays and objects.
Pass `state` to your UI (e.g. - via Component `props`). `state` will be managed
by a single application **store**.

```js
const state = {
  messages: [ ... ],
  user: { ... },
  router: { ... }
}
```

`state` is read-only. Dispatch **actions** to the store to get the next
application state. Actions can be triggered by Browser Events or Network Requests.
Think of actions as a minimal description of the event that happened in the app,
coupled with the information necessary to build the next state.

```js
const action = {
  type: "ADD_MESSAGE",
  message: "I'm learning Redux!"
}
```

Describe state mutations as **reducer** functions.

```js
const initialState = {
  messages: []
}

// Keep this function "pure". Treat inputs as read-only.
const reducer = (state = initialState, action) => {
  switch (action.type) {
    case "ADD_MESSAGE":
      // Don't change `state` directly. Return an updated copy.
      return {
        ...state,
        messages: [...state.messages, action.message]
      }
    case "DELETE_MESSAGE":
      return {
        ...state,
        messages: state.messages.filter(m => m.id !== action.messageId)
      }
    // ...
    default:
      return state;
  }
}
```
