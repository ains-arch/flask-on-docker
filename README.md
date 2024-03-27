# flask-on-docker

## Overview

This repo contains all the necessary files to host a simple web app.
The development environment configures the default Flask development server
to run on Docker with Postgres.
The production environmental also includes Nginx and Gunicorn,
and supports serving both static and user-uploaded media files via Nginx. 

<img width=100% src=upload.gif alt="gif of an image being uploaded through the web service"/>

## Build Instructions

### Development

Build the images and run the containers:

```sh
$ docker-compose up -d --build
```

Test it out at [http://localhost:1361](http://localhost:1361).

### Production

1. Create a *.env.prod* file in the root folder of the project. Choose a username and password.

```sh
FLASK_APP=project/__init__.py
FLASK_DEBUG=0
DATABASE_URL=postgresql://$YOUR USERNAME HERE:$YOUR PASSWORD HERE@db:5432/hello_flask_prod
SQL_HOST=db
SQL_PORT=5432
DATABASE=postgres
APP_FOLDER=/home/app/web
```

2. Create a *.env.prod.db* file in the root folder of the project. Use the same username and password.

```sh
POSTGRES_USER=$YOUR USERNAME HERE
POSTGRES_PASSWORD=$YOUR PASSWORD HERE
POSTGRES_DB=hello_flask_prod
```

3. Build the images and run the containers:

```sh
$ docker-compose -f docker-compose.prod.yml up -d --build
```

Test it out at [http://localhost:1447](http://localhost:1447)!
