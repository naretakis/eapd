## The Technology We Are Using for a Nontechnical Audience

This page is designed to provide information for this project accessible for folks besides our developers. It is heavily sourced from our [[existing documentation|Development index]], but will focus on abstracting the concepts and answer questions about how we are using the technology within the application.

## Cloud Infrastructure

### Amazon Web Services (AWS)

_Placeholder for our selected AWS approach._

_Placeholder for our Dev and Prod environments description._

### Deployment

_[What is Circle CI, and why are we using it?](https://circleci.com/blog/what-is-continuous-integration/)_
Basically, Continuous Integration means multiple developers pushing small, frequent changes to a shared repository or ‘master’. They are integrating changes continuously, rather than periodically, and thus–ta da!–Continuous Integration. If your tests pass, then you can deploy your code to development, staging, production, etc., automatically. (Sourced from [CircleCi.com](CircleCi.com))

We are using [CircleCI](https://circleci.com/gh/18F/workflows/cms-hitech-apd) to
automate our tests as well as our deployments. We have some more [[documentation|Development deployment]] that takes about our deployments in a little more detail.

### Front end

_[What is React and why we are using it?](reactjs.org/)_ React makes it painless to create interactive UIs. Design simple views for each state in your application, and React will efficiently update and render just the right components when your data changes. Declarative views make your code more predictable and easier to debug. (Sourced from [reactjs.org/](reactjs.org/))

The front end is built in [React](https://reactjs.org/), and uses the following
libraries:

- [react-router](https://www.npmjs.com/package/react-router) for page routing
- [Redux](https://redux.js.org/) for internal state management
- [Webpack](https://webpack.js.org/) for bundling the app into a deliverable
- [okta-auth-js](https://github.com/okta/okta-auth-js) for authenticating with Okta

(We have more detailed
[[documentation about how our frontend build is configured|Development frontend#Building]],
too).

We use the [CMS Design System](https://design.cms.gov/), as the foundation
for styling, and add additional stylesheets where appropriate. We build our
custom styles in [Sass](https://sass-lang.com/), a superset of the CSS standard
that provides a lot of convenient and reusable patterns to cut down on new
development time. Sass is converted into standard CSS as part of the build
process.

For testing, we use [Jest](https://facebook.github.io/jest/) as the test runner
and [Enzyme](http://airbnb.io/enzyme/) and [React-Testing-Library](https://testing-library.com/docs/react-testing-library/intro/) as React renderers.

## API

The API is built on [Express](https://expressjs.com/) using a
[PostgreSQL](https://www.postgresql.org/) database, and a handful of libraries:

- [jwt-verifier](https://github.com/okta/okta-oidc-js/tree/master/packages/jwt-verifier) for verifying the jwt authorization tokens received with the requests that were supplied by Okta
- [okta-sdk-nodejs](https://github.com/okta/okta-sdk-nodejs) for interacting with Okta to retrieve user profiles
- [Knex](http://knexjs.org/) for interacting with the database

For testing, we use [node-tap](http://www.node-tap.org/) as the runner and
assertions, and [Sinon.JS](sinonjs.org) for mocking.

If you want to get a little deeper into how the API works, we have documentation
about:

- [[configuring the back end app (environment variables and stuff like that)|Development backend#Runtime configuration]] 
- [[our authorization model|Development-authentication-and-authorization#Authorization]]
- [[how we handle authentication|Development-authentication-and-authorization#Authentication]]

The API is also documented with [OpenAPI](https://www.openapis.org/). To see the
spec document, once the API is running, you can browse to its `/open-api`
endpoint. You can also use a hosted version of
[Swagger UI](http://petstore.swagger.io/) to get a nicer visualization.

## Database

The current database model is presented here. The `knex_*` tables are used to manage migration versions by our database interaction library.

![database-diagram](https://images.zenhubusercontent.com/5f18484c4aa7386e0e7413c8/e1b61b78-6a89-4301-9a4a-1682cc8d7d41)

## Testing

_Placeholder for more information regarding testing_

We also have [[documentation about how to run tests|Development accessibility, testing, and linting#Testing]].

## Linting

_[What is linting, and how do we use it?](https://eslint.org/docs/about/)_ Code linting is a type of static analysis that is frequently used to find problematic patterns or code that doesn’t adhere to certain style guidelines. ESLint was created was to allow developers to create their own linting rules. ESLint is designed to have all rules completely pluggable. The default rules are written just like any plugin rules would be. They can all follow the same pattern, both for the rules themselves as well as tests. (sourced from [eslint.org](eslint.org))

We use [eslint](https://eslint.org/) to analyze our JavaScript files and find
patterns / code that doesn't adhere to our style rules. Our rules are based on
[AirBnb's style guide](https://github.com/airbnb/javascript) and
[Prettier](https://github.com/prettier/prettier).

## Accessibility

We use [tota11y](http://khan.github.io/tota11y/) to manually test our pages during development for accessibility violations. Tota11y helps visualize how your site performs with assistive technologies. The process of testing for accessibility (a11y) is often tedious and confusing. In many cases, developers must have some prior accessibility knowledge in order to make sense of the results. Instead, tota11y aims to reduce this barrier of entry by helping visualize accessibility violations (and successes), while educating on best practices. Tota11y is a single JavaScript file that inserts a small button in the bottom corner of your document (sourced from [http://engineering.khanacademy.org/posts/tota11y.htm](http://engineering.khanacademy.org/posts/tota11y.htm)).

We also utilize
[eslint-plugin-jsx-a11y](https://github.com/evcohen/eslint-plugin-jsx-a11y) for
automated checks for a11y rules within React components.
