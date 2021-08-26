
# Setup (Docker)

## Hardware requirements

Hubgrep.io currently runs on a vServer with two cores and 8GB Ram, and uses about 60GB disk space - but since it needs to update the search index, it needs at least twice as much disc space.
These are pretty much the minimum specs if you want to host a copy of a search index of all of gitubs public repositories (about 180 million in august 2021.)

To run a search index only containing everything else, a raspberry should be fine.


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

On the first start you need to run 

    ./search_init.sh

This will spin up postgres, initialize the database, fetches a copy of the data needed to create the search index - and creates the first search index!
After the script is finished, you should have hubgrep running on port `8080`, you you didnt change anything.

## Updating the search index

To update the search index, run

    ./search_update.sh

This will essentially do the same thing as `./search_init.sh`, but skips database initialization, and builds a second index while the first one is still up and working.
When finished, it rotates the indexes and discards the old one, minimizing the downtime.


## Updating to a new version

To build a new version of the docker image, you need to run

    docker-compose -f docker-compose.prod.yml build
    # or
    docker-compose -f docker-compose.prod.yml up -d --build
  
Note: This is not needed the first time you start, but to trigger building the container after an update to a new version this is neccessary.

After an update it might be neccessary to update the database structure.
Easiest is, to run a new shell in the container:

    docker-compose -f docker-compose.prod.yml run --rm service /bin/bash

and in there, run:

    flask db upgrade

Which migrates the database, making it usable for the current version of HubGrep.


## Starting the containers

To start the containers (HubGrep and needed services), run

    docker-compose -f docker-compose.prod.yml up

(or add a `-d` to detach).

Afterwards, the service should be accessible on `http://yourip:8080`.


## Nginx setup

You likely want to serve via web-server, not with gunicorn (which serves the app, unless changed in the docker-compose file). 

We recommended you do this so that you can add a certificate for https, and serve assets more efficiently. 

If you use the `docker-compose.prod.yml` file, there is already something set up:
On startup, it links the built assets to `./static` on the host, so you can set up your webserver to serve from there.

Alternatively, you can run `flask cli copy-static /some/path` inside the container.

You can find an example nginx config [here](./nginx_example.conf).


## Customizing the About Page

Set environment variable `HUBGREP_ABOUT_MARKDOWN_FILE` to a path containing a markdown file,
and it will be rendered into the about page.


