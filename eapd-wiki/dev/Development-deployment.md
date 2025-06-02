Our builds and deployments are managed via a CI/CD process using
[CircleCI](https://circleci.com/gh/18F/workflows/cms-hitech-apd). Deployments
follow this general, high-level workflow:

![CI/CD diagram](diagrams/CI-CD-steps.jpg)

# Production deploys

A production build will begin when a new tag is pushed to Github that begins with `v`. These tags may be created manually or via the Github "release" tool, and may occur on any branch. Before a deployment into production occurs, the following build steps must succeed:

- **Dependency vulnerability scans pass** - The backend and frontend production dependencies are scanned for known vulnerabilities, and none are found.

- **API endpoint tests pass** - All of the API endpoints are tested to verify the expected behavior against a live database with known data.

- **Backend unit tests pass** - Unit tests, without a database, verify expected behavior of smaller units of the backend.

- **Frontend build succeeds** - The process for building the webpack source into distributable libraries is successful, a useful quality test.

- **Frontend unit tests pass** - Unit tests using a test renderer, verify expected behavior of individual UI components and utility helpers.

- **Code lint passes** - Backend and frontend code is run through a linter to enforce code quality and everything passes.

- **Build artifacts are saved** - The source code, all dependencies, and only necessary database migrations are bundled into a zip file. This will be used to deploy the backend.

- **YAML is valid** - The YAML files, used to drive a significant amount of the textual content on the frontend, are all valid YAML syntax.

The build and deployment use the following environment variables:

| Name                                | Description                                                                                                                                       |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `AWS_ACCESS_KEY_ID`                 | AWS access key ID of the user to run as. Currently using a special-purpose CI/CD account.                                                         |
| `AWS_SECRET_ACCESS_KEY`             | AWS secret access key value for the user.                                                                                                         |
| `CODECOV_TOKEN`                     | Access token from [codecov.io](codecov.io) for reporting code coverage metrics from the backend and frontend unit tests.                          |
| `PRODUCTION_API_AWS_ACCESS_KEY_ID`  | AWS access key ID the API should use for reading and writing files to S3.
| `PRODUCTION_API_AWS_AMI`            | ID of the AWS image AMI to use for building the backend EC2 instance.                                                                             |
| `PRODUCTION_API_FILES_S3_BUCKET`    | The name of the S3 bucket to read/write files. This is ***ONLY*** the bucket name, not the S3 URI.
| `PRODUCTION_API_AWS_REGION`         | AWS region to deploy the backend EC2 instance into.                                                                                               |
| `PRODUCTION_API_AWS_SECURITY_GROUP` | ID of AWS security group to attach to the backend EC2 instance.                                                                                   |
| `PRODUCTION_API_AWS_SECRET_ACCESS_KEY` | AWS secret access key value for the S3 key.
| `PRODUCTION_API_AWS_SUBNET`         | ID of the AWS subnet to attach the backend EC2 instance to.                                                                                       |
| `PRODUCTION_API_AWS_TARGET_GROUP`   | ARN of the AWS target group to add the backend EC2 instance to.                                                                                   |
| `PRODUCTION_API_DATABASE_URL`       | PostgreSQL database URL that the backend should connect to.                                                                                       |
| `PRODUCTION_API_PBKDF2_ITERATIONS`  | Number of iterations to use when hashing user passwords. This should be calibrated to take about 300 milliseconds on the deployed infrastructure. |
| `PRODUCTION_API_PORT`               | Port number the backend API should listen on. This must match the port number the AWS target group is configured to use.                          |
| `PRODUCTION_API_SESSION_SECRET`     | Session secret key used by the backend API to sign and verify JWT session tokens.                                                                 |
| `PRODUCTION_WEB_API_URL`            | URL of the production API, to be injected into the frontend when it is built. Can be a relative URL (by leaving out the protocol) or absolute (by adding the protocol). |
| `PRODUCTION_WEB_AWS_REGION`         | AWS region to deploy the frontend EC2 instance into.                                                                                              |
| `PRODUCTION_WEB_AWS_S3_BUCKET`      | AWS S3 bucket URL to use (e.g., `s3://bucket-name`)                                                                                               |
| `PRODUCTION_OKTA_DOMAIN`            | Okta domain url                                                                                               |
| `PRODUCTION_OKTA_SERVER_ID`         | Okta Server ID                                                                                               |
| `PRODUCTION_OKTA_CLIENT_ID`         | Okta Client ID                                                                                               |
| `PRODUCTION_OKTA_API_KEY`           | Okta API Key    |
| `PRODUCTION_JWT_SECRET`             | Secret used for encrypting the JWT.  DO NOT SHARE THIS|


As detailed in the [[Infrastructure Architecture]] documentation, the
production environment uses an S3 bucket for the frontend and an EC2 instance
for the backend.

### High-level overview

![high-level overview diagram of staging/production deployment process](diagrams/production-deployment.jpg)

### Frontend

The frontend deployment takes the artifacts from the "run frontend build"
step and runs the `aws s3 sync` command to push newly-created files to the
production S3 bucket. The `sync` command is also configured to delete any
files from the S3 bucket that are no longer part of the build. When this
is finished, the frontend deployment is done.

### Backend

The backend deployment is a bit more involved. First, the existing production
EC2 instance is identified and its ID is stored. Then, a new EC2 instance
is created, given a startup script to execute once it's running. This script
installs Node.js, pulls the built backend artifacts from CircleCI,
runs database migrations, sets up the
[PM2 process manager](http://pm2.keymetrics.io/), and starts the API. Once the
instance is ready, it is added as a target to the load balancer. It can take a
few minutes for the new instance to be "healthy" in the load balancer, but when
that happens, the old EC2 instances is terminated.

The EC2 instance is given a tag named `environment` and value `production` to make it easy to identify.

There are additional build steps in the production (and staging) builds, as shown in this diagram:

![deployment diagram](diagrams/deploy.mmd.png)

# Staging deploys

A staging build will begin when a new commit is pushed to Github on the `main` branch. A staging build and deployment is identical to a production build and deployment as described above, except it uses a different set of environment variables to configure where it is deployed:

| Name                             | Description                                                                                                                                       |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `AWS_ACCESS_KEY_ID`              | AWS kccess key ID of the user to run as. Currently using a special-purpose CI/CD account.                                                         |
| `AWS_SECRET_ACCESS_KEY`          | AWS secret access key value for the user.                                                                                                         |
| `CODECOV_TOKEN`                  | Access token from [codecov.io](codecov.io) for reporting code coverage metrics from the backend and frontend unit tests.                          |
| `STAGING_API_AWS_ACCESS_KEY_ID`  | AWS access key ID the API should use for reading and writing files to S3.
| `STAGING_API_AWS_AMI`            | ID of the AWS image AMI to use for building the backend EC2 instance.                                                                             |
| `STAGING_API_FILES_S3_BUCKET`    | The name of the S3 bucket to read/write files. This is ***ONLY*** the bucket name, not the S3 URI.
| `STAGING_API_AWS_REGION`         | AWS region to deploy the backend EC2 instance into.                                                                                               |
| `STAGING_API_AWS_SECURITY_GROUP` | ID of AWS security group to attach to the backend EC2 instance.                                                                                   |
| `STAGING_API_AWS_SECRET_ACCESS_KEY` | AWS secret access key value for the S3 key.
| `STAGING_API_AWS_SUBNET`         | ID of the AWS subnet to attach the backend EC2 instance to.                                                                                       |
| `STAGING_API_AWS_TARGET_GROUP`   | ARN of the AWS target group to add the backend EC2 instance to.                                                                                   |
| `STAGING_API_DATABASE_URL`       | PostgreSQL database URL that the backend should connect to.                                                                                       |
| `STAGING_API_PBKDF2_ITERATIONS`  | Number of iterations to use when hashing user passwords. This should be calibrated to take about 300 milliseconds on the deployed infrastructure. |
| `STAGING_API_PORT`               | Port number the backend API should listen on. This must match the port number the AWS target group is configured to use.                          |
| `STAGING_API_SESSION_SECRET`     | Session secret key used by the backend API to sign and verify JWT session tokens.                                                                 |
| `STAGING_WEB_API_URL`            | URL of the staging API, to be injected into the frontend when it is built. Can be a relative URL (by leaving out the protocol) or absolute (by adding the protocol). |
| `STAGING_WEB_AWS_REGION`         | AWS region to deploy the frontend EC2 instance into.                                                                                              |
| `STAGING_WEB_AWS_S3_BUCKET`      | AWS S3 bucket URL to use (e.g., `s3://bucket-name`)                                                                                               |
| `STAGING_OKTA_DOMAIN`            | Okta domain url                                                                                               |
| `STAGING_OKTA_SERVER_ID`         | Okta Server ID                                                                                               |
| `STAGING_OKTA_CLIENT_ID`         | Okta Client ID                                                                                               |
| `STAGING_OKTA_API_KEY`           | Okta API Key                                                                                               |
| `STAGING_JWT_SECRET`             | Secret used for encrypting the JWT.  DO NOT SHARE THIS|


The EC2 instance is given a tag named `environment` and value `staging` to make it easy to identify.

# Preview deploys

A preview build will begin when a new commit is pushed to Github on a branch that is **_not_** `main` and that is part of a pull request. Before the deployment happens, the following build steps must succeed:

- **Dependency vulnerability scans pass** - The backend and frontend production dependencies are scanned for known vulnerabilities, and none are found.

- **Frontend build succeeds** - The process for building the webpack source into distributable libraries is successful, a useful quality test.

- **YAML is valid** - The YAML files, used to drive a significant amount of the textual content on the frontend, are all valid YAML syntax.

- **OWASP Zap Scan** - This is not a required step, but by default runs a scan on the application to discover security risks and vulnerabilities of the system and its data. This scan be opted out of by using the ignore-owasp Git tag. If you wish to have your deploy without the scan tag your commit with the ignore-owasp tag and then push. This should only be done if you have recently passed the OWASP scan and are making minor changes to your preview deploy. 

![high-level diagram of preview deployment process](diagrams/preview-deployment.jpg)

Preview deploys are entirely self-contained in a single EC2 instance. Similar
to production backend deploys, the process begins by identifying any existing
EC2 instances for the same pull request. Then a new EC2 instance is created
with a startup script. This script is slightly different. It first generates
self-signed certificates to use for SSL. Then it installs Node.js, nginx, and
PostgreSQL and configures them.

The nginx configuration enables SSL using the self-signed certificates, sets
the root web path, and creates a proxy to pass requests to `/api` on to the
local port 8000, which is where the API will be listening. PostgreSQL is
configured to allow local network connections, sets a password, and creates
a database.

Then it fetches the app source code, installs runtime dependencies, runs
database migrations and development seeds, sets up the
[PM2 process manager](http://pm2.keymetrics.io/), and starts the API. It also
builds the frontend using `/api` as the API URL. Once the instance is ready,
its public DNS address is fetched and posted as a Github comment on the pull
request that is being previewed. Finally, any instances that already existed
for the same pull request are terminated.

Preview deployments are terminated when a new push is made to the same branch.
There is also a scheduled job that runs once per hour that terminates preview
deployments that are associated with pull requests that have been closed.

Preview EC2 instances are given a pair of tags. One named `environment` has the value `preview` and another named `github-pr` gets the associated PR number as its value. These help make the instances identifiable.

The following environment variables need to be available in the CircleCI
environment where the deployment will happen:

| Name                            | Description                                                                                                                                       |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `AWS_ACCESS_KEY_ID`             | AWS kccess key ID of the user to run as. Currently using a special-purpose CI/CD account.                                                         |
| `AWS_SECRET_ACCESS_KEY`         | AWS secret access key value for the user.                                                                                                         |
| `CODECOV_TOKEN`                 | Access token from [codecov.io](codecov.io) for reporting code coverage metrics from the backend and frontend unit tests.                          |
| `PREVIEW_AWS_AMI`               | ID of the AWS image AMI to use for building the EC2 instance.                                                                                     |
| `PREVIEW_AWS_REGION`            | AWS region to deploy the EC2 instance into.                                                                                                       |
| `PREVIEW_AWS_SECURITY_GROUP`    | ID of AWS security group to attach to the EC2 instance.                                                                                           |
| `PREVIEW_AWS_SUBNET`            | ID of the AWS subnet to attach the EC2 instance to.                                                                                               |
| `PREVIEW_API_PBKDF2_ITERATIONS` | Number of iterations to use when hashing user passwords. This should be calibrated to take about 300 milliseconds on the deployed infrastructure. |
| `PREVIEW_OKTA_DOMAIN`            | Okta domain url                                                                                               |
| `PREVIEW_OKTA_SERVER_ID`         | Okta Server ID                                                                                               |
| `PREVIEW_OKTA_CLIENT_ID`         | Okta Client ID                                                                                               |
| `PREVIEW_OKTA_API_KEY`           | Okta API Key                                                                                               |
