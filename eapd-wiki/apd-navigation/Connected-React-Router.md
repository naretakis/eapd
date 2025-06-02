> Synchronize router state with redux store through uni-directional flow (i.e. `history` -> `store` -> `router` -> `components`).

[source](https://github.com/supasate/connected-react-router)

```jsx
import React from 'react';
import { Provider } from 'react-redux';
import { ConnectedRouter } from 'connected-react-router';

import App from './App';

// note: configuration of store, history, and reducers is intentionally omitted.

const Root = ({ history, store }) => {
  return (
    <Provider store={store}>
      <ConnectedRouter history={history}>
        <App />
      </ConnectedRouter>
    </Provider>
  );
};

export default Root;
```

Your state tree now has the following nodes:

```js
const state = {
  router: {
    location: {
      pathname: '/',
      search: '',
      hash: '',
      key: '',
      query: {}
    },
    action: ''
  }
}
```

Subscribe to location changes app (e.g. - `pathname`), and update state.

```js
import { LOCATION_CHANGE } from 'connected-react-router';

const reducer = (state = initialState, action = {}) => {
  switch (action.type) {
    case LOCATION_CHANGE:
      // ...
      return {
        ...state,
        updatedProp
      }

    default:
      return state
  }
}

export default reducer
```
