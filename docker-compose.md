# Docker Compose

## Docker Compose File

- `version` for specifying support version of docker-compose with docker engine.

- `services` where all the services and containers need to be defined. service needs to be specified/listed using their desired names. 

    - Each service has `build` key which points to docker file of that container.

    - If any service doesn't have dockerfile and needs to use prebuild images on docker hub, then `image` key needs to be used. 

    - `ports` key will specify the port mappings for particular service with list of port mappings with `-` syntax.

    - For specifying environment variables, `environment` is used in a service in a list syntax (or in property-value syntax) specifying key and values.

    - In any service, `volumes` can be provided in order to persist data.

    - `command` overrides the default entrypoint command.

- `volumes` need to be defined which are used in `services` with property-value syntax with no value.

## Build images in using docker-compose

> `docker-compose build` or for no caching `docker-compose build --no-cache`.

## Running the container using docker compose file

> `docker-compose up -d` Here `-d`(optional) for deteched mode or combining the up and build by `docker-compose up --build`.

## For logs in docker compose

> `docker-compose logs`