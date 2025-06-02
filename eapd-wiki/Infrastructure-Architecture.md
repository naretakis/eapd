This page describes the infrastructure architecture of the app, as hosted in
[Amazon AWS](https://aws.amazon.com/).

# Production and staging environments

[[diagrams/aws.prod.png]]

## Frontend

The frontend is made up of static assets, such as HTML pages, Javascript files,
stylesheets, etc. These assets are hosted in an
[AWS S3 bucket](https://aws.amazon.com/s3/) with static website hosting
enabled. Metadata is added to the `index.html` file with key `Cache-Control`
and value `max-age=0` to prevent CloudFront from cacheing it, so redeploys are
live immediately. There is one bucket per deployment environment. On
redeployment, the S3 bucket is synced with the new frontend code, and files
that no longer exist in the frontend are removed from the bucket. CloudFront
also routes all responses through a Lambda@Edge function that adds browser
security headers, such as `Content-Security-Policy`, `X-Frame-Options`, etc.

(Note that the Lambda@Edge functions must be located in the `us-east-1` AWS
region and must **_NOT_** use the Node 12 runtime because it is not supported
by Lambda@Edge yet.)

## Backend

The backend is hosted in an [AWS EC2](https://aws.amazon.com/ec2/) instance
with access via an
[Elastic Load Balancer (ELB)](https://aws.amazon.com/elasticloadbalancing/).

The API is a [Node.js](https://nodejs.org) app using the
[Express.js framework](https://expressjs.com). It accepts HTTP `GET`, `PUT`,
`POST`, and `DELETE` requests for various endpoints. It also handles setting
appropriate CORS headers. The API queries the database to set and retrieve data
as needed to serve its requests. There is one EC2 instance per environment.

## Database

The database is hosted in an [AWS RDS](https://aws.amazon.com/rds/) instance of
[PostgreSQL](https://www.postgresql.org/). The database is configured such that
only the appropriate backend EC2 instance can access it.

# Preview environments

Each pull request is a self-contained environment consisting of a single EC2
instance. The instance has an nginx web server installed that is configured
to only accept SSL connections. This SSL connection uses a self-signed SSL
certificate. The nginx web server proxies requests to `/api/*` endpoints to
the API running as a Node.js app listening on local port 8000. For all other
requests, nginx serves static content from the frontend. The API uses a
PostgreSQL database installed locally on the EC2 instance. The database is
seeded with development data.

[[diagrams/aws.preview.png]]

One strong advantage to this approach for preview environments is that they
are **_strongly_** isolated from each other and from all other environments.
