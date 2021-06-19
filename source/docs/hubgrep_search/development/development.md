

## Development Setup

### Web-frontend:

    docker-compose up

Navigate to `0.0.0.0:8080` in your browser to search. The config for what is included is found in `docker-compose.yml`.


### CLI:

To use the CLI, you must first have a shell inside a running container. Run:

    docker-compose run --rm service /bin/bash

Once inside, run:

    flask cli search <TERMS>


## Testing

Using pytest and pytest-coverage, run:

    ./manage.sh test
    

