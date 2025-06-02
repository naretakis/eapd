`<ConnectedWaypoint />` updates `store.router.location.hash` (the URL
`#fragment`) with the id of the HTML element, when it is 90% of the height from
the bottom of the browser window.

The `history` API methods provided by `connected-react-router` are: `push`,
`replace`, `go`, `goBack`, `goForward`. It is important to use `replace` in this
instance, since we are updating the URL to reflect navigating to a section of
a page, and not navigating to another page.

```jsx
import React, { Fragment } from 'react';
import { connect } from 'react-redux';
import { Waypoint } from 'react-waypoint';
import { replace as actualReplace } from 'connected-react-router';

const ConnectedWaypoint = ({ children, id, location, replace }) => (
  <Fragment>
    <Waypoint
      bottomOffset="90%"
      fireOnRapidScroll={false}
      onEnter={() => replace({ ...location, hash: id })} />
    {children}
  </Fragment>
);

const mapStateToProps = ({ router }) => ({
  location: router.location
});

const mapDispatchToProps = {
  replace: actualReplace
};

export default connect(
  mapStateToProps,
  mapDispatchToProps
)(ConnectedWaypoint);
```

## Example

Scrolling to the `<Waypoint id="prev-activities-table" />` component triggers
the `onEnter` function, which updates `store.rouer.location.hash`.

[[waypoint-component.png]] [[waypoint-component-state.png]]
