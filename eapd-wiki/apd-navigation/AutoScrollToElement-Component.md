When visiting a link that includes a `#fragment`, we need a mechanism to bring
that HTML element into focus.

`<AutoScrollToElement />` watches for changes in `store.router.location` and
scrolls to the top of the page when navigating to a new page. Then, scrolls to
the element identified by `store.router.location.hash`, if present.

```jsx
import React from 'react';
import { connect } from 'react-redux';

const AutoScrollToElement = ({ location, action }) => {
  const { hash } = location;

  React.useEffect(() => {
    if (action !== 'PUSH') return; // only execute on PUSH action
    window.scrollTo(0, 0);
    const element = hash ? document.querySelector(hash) : null;
    if (element) {
      element.scrollIntoView();
      window.scrollBy(0, -50); // compensate for header
    }
  }, [location]);

  return null;
};

const mapStateToProps = ({ router: { location, action } }) => ({
  location,
  action
});

export default connect(mapStateToProps)(AutoScrollToElement);
```

## Example

Clicking the "Prior Activities Overview" link in the `<Nav />`, takes you to
the `/apd/previous-activites` page, and `<AutoScrollToElement />` scrolls to the
element identified by the URL fragment (hash): `#prev-activities-outline`.

[[AutoScrollToElement-Component.png]]
