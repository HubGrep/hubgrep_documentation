
# Setup (Docker)

## Creating your configuration

Create a config by copying `.env.dist` to `.env` and add the missing values.
You can check [Environment Variables](environment_variables), but it should be mostly self-explanatory.

Next, there is a `docker-compose.prod.yml` file, which would start an instance of HubGrep. 
It contains redis db for caching, and postgres to store user data such as service-hosters which have been added.

You should check if the dockerfile contain the configuration you want 
(maybe you want to use another database, for example).

Also, it might be a good idea to make a copy of this dockerfile, so that you dont run into conflicts when pulling new 
versions of this repo.


## First start

To build an image with generated assets and source code baked in, 
run:

    docker-compose -f docker-compose.prod.yml build
  
Note: This is not needed the first time you start,
but to trigger building the container after an update to a new version this is neccessary.

To start the containers (HubGrep and needed services), run

    docker-compose -f docker-compose.prod.yml up

(or add a `-d` to detach).

On first setup, you need to setup the database and the admin user.
Easiest is, to run a new shell in the container:

    docker-compose -f docker-compose.prod.yml run --rm service /bin/bash

and in there, run:

    flask db upgrade
    flask cli init

The first command migrates the database (creating the database structure that we use), 
the second one creates an admin user as defined in the environment variables.


Afterwards, the service should be accessible on `http://yourip:8080`.


## Adding service-hosters 

Add hosting-services to enable HubGrep to search for results. Use either the web-frontend 
or the CLI. Hosting-services are tied to the current user while adding them; CLI always uses admin while web-frontend requires a login.
 
Adding via CLI (from within container shell):

    flask cli add-hoster github "https://api.github.com/" "https://github.com/" "{}"
    flask cli add-hoster gitea "https://codeberg.org/api/v1/" "https://codeberg.org/" "{}"
    flask cli add-hoster gitea "https://gitea.com/api/v1/" "https://gitea.com/" "{}"

(For gitlab, see [Adding Gitlab Instances](#adding-gitlab-instances))


## Nginx setup

You likely want to serve via web-server, not with gunicorn (which serves the app, unless changed in the docker-compose file). 

We recommended you do this so that you can add a certificate for https, and serve assets more efficiently. 

To get the static files, there is an example setup in `docker-compose.prod.yml` already.
Just uncomment the "volumes" section in the compose file, and the `STATIC_PATH` in your `.env`.
This would copy the static files to `./host_static` on startup.

Alternatively, you can run `flask cli copy-static /some/path` inside the container.

You can find an example nginx config [here](./nginx_example.conf).


## Customizing the About Page

Set environment variable `HUBGREP_ABOUT_MARKDOWN_FILE` to a path containing a markdown file,
and it will be rendered into the about page.


