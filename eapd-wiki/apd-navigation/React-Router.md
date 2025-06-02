Clicking a `<Link to={pathName}>` component renders the children of the
`<Route path={pathName}>` component.

> As you click around on the different `<Link>`s, the router renders the
> matching `<Route>`. [...] Behind the scenes a `<Link>` renders an `<a>` with
> a real href, so people using the keyboard for navigation or screen readers
> will still be able to use this app.

[source](https://reacttraining.com/react-router/web/guides/quick-start)

```jsx
import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link
} from "react-router-dom";

export default function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li><Link to="/">Home</Link></li>
            <li><Link to="/about">About</Link></li>
            <li><Link to="/users">Users</Link></li>
          </ul>
        </nav>

        {/* A <Switch> looks through its children <Route>s and
            renders the first one that matches the current URL. */}
        <Switch>
          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
          <Route path="/users" component={Users} />
        </Switch>
      </div>
    </Router>
  );
}
```
