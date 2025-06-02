# Accessibility

We use [WAVE](https://wave.webaim.org/) to quickly scan our pages during development for accessibility violations. We also utilize [eslint-plugin-jsx-a11y](https://github.com/evcohen/eslint-plugin-jsx-a11y) for automated checks for a11y rules within React components. The app must have 0 errors.

We also perform manual accessibility testing by checking keyboard navigation and screen reader behavior.

# Linting

We use [eslint](https://eslint.org/) to analyze our JavaScript files and find
patterns / code that doesn't adhere to our style rules. Our rules are based on
[AirBnb's style guide](https://github.com/airbnb/javascript) and
[Prettier](https://github.com/prettier/prettier).

# Testing

We're big fans of testing, so we're putting in lots of testing throughout this app, both frontend and backend. Here are some notes describing the tests and how to run them.

If you haven't gotten everything running yet, [[the development environment guide|Development-environment]] has good instructions on how to get started.

## Frontend

On the frontend, we use [Jest](https://facebook.github.io/jest/) as the test runner and [Enzyme](http://airbnb.io/enzyme/) and [React-Testing-Library](https://testing-library.com/docs/react-testing-library/intro/) as a React renderers. This gives us unit testing and a heads-up if any components suddenly start rendering differently. We will also use Enzyme to do feature testing, where we render a full page, click buttons, and verify expected behaviors. We use React-Testing-Library to do integration testing, where we need components that are fully rendered and connected to redux and browser actions.


To run the tests, after everything is installed, just open a command line and run:

```shell
cd web # get into the right directory!
yarn test
```

That's it! The test reporter will show a coverage table at the end so you can see what parts of the code need more tests. It will also generate an LCOV coverage report, along with an HTML render of the report, if that's the sort of thing you like to look at. It gets written to `web/coverage/lcov-report/index.html`.

## Backend

On the backend, we use [node-tap](http://www.node-tap.org/) as the test runner, assertion library, coverage reporter, and more. It's a pretty full-featured library, so we lean on it. We use this for unit tests. For end-to-end API tests, we use [Jest](https://facebook.github.io/jest/) because it has handy snapshot tools that are really great for confirming that API outputs don't unexpectedly change without having to write a mountain of fragile code to check them.

#### Unit tests

The unit tests are pretty easy to run since all external interactions are mocked (we rely heavily on dependency injection). Open a command line and run:

```shell
cd api # get into the right directory!
./unit-test.sh
```
The unit tests interface with a live DB.  As such you must actively ensure that all promises are settled and the DB connection is closed after each test suite.  Doing this is rather simple and just involves adding this snippet:
```javascript
  t.teardown(() =>{
    knex.destroy()
  })
```
This must be done even if the DB connection is not opened directly in the tests.  For example api.test.js uses the entire express API which indirectly creates a DB connection.  Thus, the test requires that knex be destroyed.

When importing the DB for any tests please ensure that you are importing db/knex.js and not importing knex directly from node_modules.  If you import directly from node_modules the connection parameters will not be set.

Finally, the DB is entirely ephemeral and is not even persisted to a volume so be aware that you must create and seed it every time you bring the containers up.  There is a script for doing this at api/setup-test-db.sh

Tap doesn't show you a coverage report table like the Jest tester, but it does generate an LCOV report and HTML render at `api/coverage/lcov-report/index.html`.


#### API/endpoint tests

Running the API tests is a little more involved because it requires that the backend actually be running with a real database setup and everything. If you're using Docker, there's a script you can run that will set everything up for you:

```shell
cd api
./endpoint-tests/endpoint.sh
```

If you're not using Docker, here are the steps:

1. Make sure you have a database called `hitech_apd_test` in your Postgres instance
2. set the `NODE_ENV` environment variable to `test`
3. set the `ENDPOINT_COVERAGE_CAPTURE` environment variable to `yes`
4. set the `TEST_DB_HOST` environment variable to the hostname/address of your Postgres instance
5. open a command line, and switch to the API directory (`cd api`)
6. run `npm run migrate` to create the database structures
7. run `npm run seed` to populate the database with test data
8. run the API, either in the background or in a separate tab/window
   - to run in the background, run `npm start &`
   - if running in a separate tab/window, be sure to set the `NODE_ENV` and `TEST_DB_HOST` in the new tab/window
9. run `npm run test-endpoints`
10. all done! You can kill the backgrounded API now

> We strongly recommend using Docker because it sets everything up for you, in
> a clean and isolated environment. It even takes care of killing the backgrounded
> API process.

The `ENDPOINT_COVERAGE_CAPTURE` environment variable lets the API know to capture
a few extra pieces of information: the list of all endpoints that are registered
with Express, and the list of all endpoints that are requested along with the HTTP
status code that is sent in response. When the endpoint tests are done, those two
lists are combined with the OpenAPI documentation to identify which registered
endpoints are not documented as well as which endpoint + response status combinations
are not tested.

## End to End Tests

### Cypress
In order to test the full end to end process we have developed a collection of cypress tests that can be executed against the running application.  These tests will perform many of the exact same actions that a user would when working with APD's.  If you are testing your own setup with your own OKTA account you will need to create a file called cypress.env.json containing a json object where the usernames are the key and the passwords are the value.  Internal users can use the copy found in Keybase. 



#### Running the tests
In order to run the tests you should already have the application running locally in docker containers.  All instructions assume that the app is running locally.  Also, note that because cypress simply uses the standard web front end, it will create and delete data.  The cypress scripts provided should prepare and seed the database used during the tests, but may delete existing work in the process.  Finally, the integrationTest folder has its own package.json so you will need to run npm install to install cypress locally.

The tests can be run as a full set with the command:
```shell
cd integrationTests
npm run cy:run
```

or one at a time in interactive mode with:
```shell
cd integrationTests
npm run cy:open
```

If you leave this open, it will rerun tests as they change which is convenient when writing new tests.

By default Cypress creates videos of test runs as well as screen shots when the test fails.  These can be found in integrationTests/cypress/videos and integrationTests/cypress/screenshots respectively.