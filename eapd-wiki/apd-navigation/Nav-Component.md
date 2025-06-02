The `<Nav />` component displays the left-hand side APD Navigation. Its `items`
are managed by the reducer at `web/src/reducers/nav.js`. We use the `pathname`
and `hash` (aka- fragment) as provided by `connected-react-router` to determine
how to expand the `<Nav />` to the current view, and to highlight the current
nav item.

```jsx
import React, { useEffect, useState } from 'react';
import { VerticalNav } from '@cmsgov/design-system-core';
import { connect } from 'react-redux';
import NavLink from '../components/NavLink';
import { generateKey as actualGenerateKey } from '../util'

const Nav = ({ generateKey, items, pathname }) => {
  // force component update when pathname changes
  const [key, setKey] = useState('');
  useEffect(() => setKey(generateKey()), [pathname]);
  return (
    <VerticalNav
      component={NavLink}
      items={items}
      key={key}
    />
  )
};

Nav.defaultProps = {
  generateKey: actualGenerateKey
}

const mapStateToProps = ({ nav, router }) => ({
  items: nav.items,
  pathname: router.location.pathname
});

export default connect(mapStateToProps)(Nav);
```

```js
const initialState = {
  activities: [],
  continueLink: null,
  items: staticItems,
  previousLink: null
};

const reducer = (state = initialState, action = {}) => {
  switch (action.type) {
    case APD_ACTIVITIES_CHANGE: {
      return {
        ...state,
        activities: action.activities
      };
    }

    case LOCATION_CHANGE: {
      const { pathname, hash } = action.payload.location;
      const url = [pathname, hash].join('');

      const items = getItems({
        activities: state.activities,
        items: state.items,
        url
      });

      return {
        ...state,
        items
      };
    }

    default:
      return state;
  }
};

export default reducer;
```
