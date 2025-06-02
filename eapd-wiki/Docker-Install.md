### Setting up environment variables

Set the following additional environment variables:

```shell
export MONGO_ADMIN_URL="mongodb://admin-user:admin-password@mongo:27017/admin" #This is only a local value.  It will be different in production
export MONGO_URL="mongodb://mongo:cms@mongo:27017/eapd?authSource=admin" #This is only a local value.  It will be different in production
export MONGO_DATABASE="eapd" #This is only a local value.  It will be different in production
```

> _**Potential WSL Gotcha:**_ If you have recently installed docker on WSL, you will need to `unset DOCKER_HOST` and then restart docker. Also, if you are running on a firewall make sure to grant access to npm and yarn.

### Create the containers

From your command line, switch to the root directory of the code and then run:
```shell
yarn install
yarn build
docker-compose up -d
```

This will do several things:

1. create a PostgreSQL database in a container
2. create a MongoDB database in a container
3. create a container for the API server, download all of its dependencies, and
   hook it up to the database
4. create a container for the web application, download all of its
   dependencies, and build it

This could take a few minutes. Once it's finished, everything is installed,
configured, and running. However, the database will still be empty, so that
needs to be created and populated with starter data. To do that, while the
docker process is still running, open a new terminal window or tab and run:

### Generating the databases and seeding the data

```shell
docker-compose exec api yarn run migrate
docker-compose exec api yarn run seed
```

This will create database tables and put some data the MongoDB and PostgreSQL databases so that the app can run,
like the list of states and territories and a user account you can use to
log into the app.

### Using the application

You should now be able to open the app at
[http://localhost:8080](http://localhost:8080). You can login with any of
the accounts that you made above. The `em@il.com` account has the role of state admin.
The rest have roles that match their usernames. This is handled in the seed
and does not need to be set in Okta.
