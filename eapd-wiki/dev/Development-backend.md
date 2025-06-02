# Architecture

The backend API is built on [Express](https://expressjs.com/) using a
[PostgreSQL](https://www.postgresql.org/) database, and a few key libraries:

- [ajv](https://www.npmjs.com/package/ajv) for document schema validation. We chose AJV because it's robust and has the features we want - namely, it can mutate the data being validated to remove properties that aren't part of the schema and it can parse the entire document to report ***all*** errors instead of just the first one.
- [jsonpatch](https://www.npmjs.com/package/jsonpatch) and [jsonpointer](https://www.npmjs.com/package/jsonpointer) for applying changes to the main APD data structure in the database and for reporting back on schema validation errors. We went with JSON Patch because it's pretty straightforward and helps us minimize the amount of data going over the wire.
- [Knex](http://knexjs.org/) for interacting with the database. We originally chose to use a query builder in case we wanted to switch database engines. In reality, we are unlikely to ever do that, but knex has proven very useful for managing database migrations. While we still use it to build queries, if not for the migrations, we might take it out.
- [jwt-verifier](https://github.com/okta/okta-oidc-js/tree/master/packages/jwt-verifier) for verifying the jwt authorization tokens received with the requests that were supplied by Okta.
- [okta-sdk-nodejs](https://github.com/okta/okta-sdk-nodejs) for interacting with Okta to retrieve user profiles.

For unit testing the API, we use [node-tap](http://www.node-tap.org/) as the runner and assertions, and [Sinon.JS](https://sinonjs.org/) for mocking. We picked node-tap because it was simple to get going, and Sinon because you just have to mock stuff sometimes. It might be worth considering gradually shifting to Jest at some point, just for consistency's sake.

The API is integration tested using Jest, relying heavily on snapshots of API results. We went with Jest because snapshots make life so much easier. The integration tests are wrapped up in Docker containers so that the testing database is separate from the dev database and can be in a known configuration when the tests begin.

The API is also documented with [OpenAPI](https://www.openapis.org/). To see the
spec document, once the API is running, you can browse to its `/open-api`
endpoint. You can also use a hosted version of
[Swagger UI](http://petstore.swagger.io/) to get a nicer visualization.

![architecture-diagram](https://user-images.githubusercontent.com/62778/180575086-4c4fff47-a225-405b-9b48-7686bc962d51.png)


# Runtime configuration

Currently, the API is configured entirely with environment variables:

- ### `DATABASE_URL`

  - This variable is only used if `NODE_ENV` is set to `production`.
  - This is the connection URL for the production environment database. In our
    current deployment setup, this is set by the CI/CD process. If it has to
    be set manually, it must be something that the underlying database client
    understands.
  - **default**: none

- ### `MONGO_URL`
  - This variable is only used if `NODE_ENV` is set to `production`.
  - This is the connection URL for the production environment database. In our
    current deployment setup, this is set by the CI/CD process. If it has to 
    be set manually, it must be something that the underlying database client
    understand.
  - **defaults**: none

- ### `OKTA_DOMAIN`

  - This is the URL to connect to Okta for authentication.
  - It can be found by asking your Okta administrator, or by going to the Okta
    admin panel and clicking `Applications -> (your application) -> General`
  - **default**: none

- ### `OKTA_SERVER_ID`

  - This is the Okta Server ID.
  - This can be found by asking your Okta administrator, or by going to the Okta
    admin panel and clicking `API -> Authorization Server`, and the value under `Name`
  - If you created your Okta application, then your Server ID is probably `default`.
  - **default**: none

- ### `OKTA_CLIENT_ID`

  - This is the Okta Client ID.
  - This can be found by asking your Okta administrator, or by going to the Okta
    admin panel and clicking `Applications -> (your application) -> General`
  - **default**: none

- ### `OKTA_API_KEY`:

  - This is the API key.
  - This can be found by asking your Okta administrator, or by going to the Okta
    admin panel and clicking `API -> Tokens -> Create Token` and creating a new
    API token and using the value in `Token Value`
  - **default**: none

- ### `LOG_CONSOLE`

  - This determines whether logging to the console is enabled. Must be the
    literal string `true` to enable. Anything else will disable.
  - **default**: true

- ### `LOG_FILE`

  - This determins whether logging to file is enabled. Must be the literal
    string `true` to enable. Anything else will disable.
  - If enabled, logs are written to the file `hitech_api.log`.
  - Logs are rotating. At 2MB, they are compressed and rotated out. A maximum
    of five log files are kept at any time.
  - **default**: false

- ### `LOG_LEVEL`
  - This is used to set the verbosity of logging.
  - Supported values: We use the default [Winston 2.x npm logging levels](https://github.com/winstonjs/winston/tree/2.x#logging-levels)
  - **default**: info

- ### `NODE_ENV`

  - This variable is used to determine which database connection configuration
    to use while the app is running. Knex reads its config information from
    `/api/knexfile.js`, which exports a few different configurations. Knex picks
    the configuration that matches the current `NODE_ENV`.
  - This variable also controls which seed data is applied to the database when
    using the Knex `seed` command.
  - Supported values:
    - `development` - used during development (surprise!). If you're developing
      with Docker, this gets set by the Docker config.
    - `test` - used during testing, eventually. Not used right now.
    - `production` - used in our staging and production environments.
  - **default**: development

- ### `PORT`

  - This is the port that the API process should listen on.
  - **default**: 8000

- ### `PROXY_TRUST`

  - This variable is used to configure whether and how Express will decode
    proxy headers to get the real client address. See [the Express documentation](https://expressjs.com/en/guide/behind-proxies.html)
    for more details
  - **default**: false

- ### `DEV_DB_HOST`

  - This variable is only used if `NODE_ENV` is set to `development`.
  - If you are developing the API code and _not_ using Docker, the default
    development database configuration won't work for you because it expects to
    use a database host that is provided by Docker. To get around that, set this
    variable to the hostname of your PostgreSQL instance.
  - **default**: `db`

- ### `DEV_DB_USER`

  - This variable is only used if `NODE_ENV` is set to `development`.
  - If you are developing the API code and _not_ using Docker, the default
    development database configuration won't work for you because it expects to
    use a database user that is configured by Docker. To get around that, set
    this variable to the username of your PostgreSQL user.
  - **default**: `postgres`

- ### `DEV_DB_PASSWORD`

  - This variable is only used if `NODE_ENV` is set to `development`.
  - If you are developing the API code and _not_ using Docker, the default
    development database configuration won't work for you because it expects to
    use a database user that is configured by Docker. To get around that, set
    this variable to the password of your PostgreSQL user.
  - **default**: `cms`


## For testing

The following environment variables are used in testing.

- ### `API_HOST`

  - This variable is used by integration tests to build URLs to connect to the
    API instance being tested.
  - **default**: localhost

- ### `API_PORT`

  - This variable is used by integration tests to build URLs to connect to the
    API instance being tested.
  - **default**: the value of the `PORT` variable, or 8000

- ### `ENDPOINT_COVERAGE_CAPTURE`

  - This variable determines whether the API will capture data on which
    registered endpoints have been tested and which status codes were seen.
    It is used primarily in integration testing but may be enabled at any time.
    Any value will enable endpoint coverage capture.
  - **default**: unset

- ### `TEST_DB_HOST`

  - This variable is only used if `NODE_ENV` is set to `test`.
  - If you are running tests and _not_ using Docker, the default test database
    configuration won't work for you because it expects to use a database host
    that is provided by Docker. To get around that, set this variable to the
    hostname of your local PostgreSQL instance.
  - **default**: none

- ### `OKTA_DOMAIN`

  - This is the URL to connect to Okta for authentication.
  - It can be found by asking your Okta administrator, or by going to the Okta
    admin panel and clicking `Applications -> (your application) -> General`
  - **default**: none

- ### `OKTA_SERVER_ID`

  - This is the Okta Server ID.
  - This can be found by asking your Okta administrator, or by going to the Okta
    admin panel and clicking `API -> Authorization Server`, and the value under `Name`
  - If you created your Okta application, then your Server ID is probably `default`.
  - **default**: none

- ## `OKTA_CLIENT_ID`

  - This is the Okta Client ID.
  - This can be found by asking your Okta administrator, or by going to the Okta
    admin panel and clicking `Applications -> (your application) -> General`
  - **default**: none

- ## `OKTA_API_KEY`:

  - This is the API key.
  - This can be found by asking your Okta administrator, or by going to the Okta
    admin panel and clicking `API -> Tokens -> Create Token` and creating a new
    API token and using the value in `Token Value`
  - **default**: none