### Setting up environment variables

Set the following additional environment variables:

```shell
export NODE_ENV=development
export WEB_PORT=8080
export API_URL=http://localhost:8081
export PORT=8081
export DEV_DB_HOST=localhost
export DEV_DB_USER=eapd
export DEV_DB_PASSWORD=cms
export MONGO_ADMIN_URL="mongodb://admin-user:admin-password@localhost:27017/admin"
export MONGO_URL="mongodb://mongo:cms@localhost:27017/eapd?authSource=admin"
export MONGO_DATABASE=eapd
```

### Downloading the dependencies

From your command line, switch to the root directory of the code and
then run these commands:

```
yarn install
yarn build
```

This will download and install the dependencies for the web application and the
API server. They're not started yet, though. 

### Setting up PostgreSQL

Next, you need to make sure
[PostgreSQL](https://www.postgresql.org/) is installed and running (or that you
have an available connection to a PostgreSQL database somewhere else).

WSL users may find additional guidance on installing databases at the [Microsoft WSL Support Site](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-database).

> _**Installing Postgres on Unix/WSL:**_ 
```shell
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
```

Next, configure your PostgreSQL instance to support the app. You will need to
create a new database called `hitech_apd`, create an eAPD user, and assign it
full permissions to the new database. You can do that from the `psql` shell.

> _**Note:**_ It is not strictly necessary to create a new PostgreSQL user. You
can use an existing user account if one is available. This is configured in
the environment variables below.

> _**Potential Gotcha:**_ 
```shell
# make sure the postgresql is running
sudo service postgresql start

# give your user permission for psql
sudo -u postgres psql postgres
```

```shell
# opens the PostgreSQL shell
psql

# From inside the psql shell:
CREATE DATABASE hitech_apd;
CREATE ROLE eapd WITH PASSWORD 'cms' LOGIN;
GRANT ALL PRIVILEGES ON DATABASE hitech_apd TO eapd;
```

### Setting up MongoDB

Next, you need to make sure [MongoDB](https://docs.mongodb.com/manual/installation/) is installed and running (or that you have an available connection to a MongoDB database somewhere else). Note: If you are running MongoDB locally, you will need to open a separate command-line window.

You will need to set some environment variables that will be used by a script and then run the script to create the databases for you.

```shell
# opens the MongoDB shell
mongo

# From inside the MongoDB shell:
## Switch to admin database
use admin

## Run this script from the shell to create "admin-user" user
db.createUser({
    user: "admin-user",
    pwd: "admin-password",
    roles: [
        "userAdminAnyDatabase",
        "dbAdminAnyDatabase",
        "readWriteAnyDatabase"
    ] 
});

## Run this script from the shell to create "mongo" user
db.createUser({
    user: "mongo",
    pwd: "cms",
    roles: [{ role: 'dbOwner', db: "eapd" }]
});

## Switch to eapd database
use eapd;

## Create Database Collections
db.createCollection('apds');
db.createCollection('migrations');
```

### Generating the databases and seeding the data 

One you have PostgreSQL, MongoDB, and Okta setup, and your environment variables set, you can
setup the database by running:

```
cd api
yarn run migrate
yarn run seed
```

This will create database tables and put in some data the app needs to run,
like the list of states and territories and a user account you can use to
log into the app.

### Starting the servers

Now you're ready to run the app. You will need two command line windows,
because both the API server and the web application will run until you stop
them, so you can't run both in the same window (unless you want to put one in
the background, but that's beyond the scope of this README).

From one command line window, switch to the directory where you put the code,
then run:

```shell
cd api
yarn run start-dev
```

That starts up the API server. It should be running at
[http://localhost:8081](http://localhost:8081). 

From another command-line window, switch
to the directory where you put the code and run:

```shell
cd web
yarn run start
```

That starts up a special server that will build and serve the web application.

### Using the application

You should now be able to open the app at
[http://localhost:8080](http://localhost:8080). You can login with any of
the accounts that you made above. The `em@il.com` account has the role of state admin.
The rest have roles that match their usernames. This is handled in the seed
and does not need to be set in Okta.

You can also play with setting any of the others you want, but be aware that
setting some of them incorrectly can cause the app to fail.