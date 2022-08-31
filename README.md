# Docker

## Version Details of Docker

> `docker version`

> For any docker cmd, for hints and help, use `--help` at the end.

## For creating image using `Dockerfile` (basic) with tag name

> `docker build -t <image-tag/name>:<tag-name> <Context directory path>`

> `docker build -t <image-tag/name>:<tag-name> -f <dockerfilename> <Context directory path>`

### Example: `docker build -t hello-docker .`

## Listing all images

> `docker images` or `docker image ls`

## To run any image

> `docker run <image-name>

### Example: `docker run hello-docker`

## To run image in interactive mode

> `docker run -it <image-name>`

### Example: `docker run -it ubuntu`

For root user, `#` sign is used in shell and for other users `$` is used.

## To run image in interactive mode with starting CMD

> `docker run -it <image-name> <starting-cmd>`

### Example: `docker run -it node bash`

## Listing all running containers (processes)

> `docker ps`

## Listing all containers (running and stopped)

> `docker ps -a`

## Starting stopped container again.

> `docker start <container_id>`

## Starting stopped container again with interactive mode.

> `docker start -i <container_id>`

## To pull image from docker hub

> `docker pull <username/repo-name>`

## To Execute bash session inside a container

> `docker exec -it <container_id> bash`

## To Execute bash session inside a container with user other than root

> `docker exec -it -u <username> <container_id> bash`

The prompt will have `$` in terminal.

## Writing instructions for building images

- `FROM` - used for pulling base image on the top of which application needs to be run.

- `COPY` - copy `one` or `more` `files` or `directories` from `current directory` (`local` PC) into `image`. We `cannot copy` anything `outside` of this local directory. When we execute `build` CMD, `docker client` sends `contents` of this dir to `docker engine`. This is called `build context` (`contents` of local Dir). It is also called `context directory`. Then `docker engine` will start executing the cmds in `Dockerfile` one by one. So `docker engine` doesn't have access to any contents outside this dir (local PC one).

- `ADD` - same as `COPY`, but two additional features. With `ADD`, we can add a file from `URL`. If we pass a compressed file, then `ADD` will automatically uncompress it into the image dir. Always use `COPY`, unless these additional features needed.

- `WORKDIR` - change working directory.

- `RUN` - Run any CMDs which we normally run in terminal.

- `ENV` - To set env variables. `ENV <key>=<value>`.

- `EXPOSE` - To what port this container be listening on.

- `USER` - cmd to set user.

- `CMD` - Entry to run our app on container. `RUN` instruction is build time instruction, so executed at the time of building image. `CMD` instruction is run time instruction, so it is executed when starting a container. `CMD` instruction has 2 forms. one is `shell form` and other is `execute form` which take array of strings. For `shell form`, docker will execute the cmd in a separate shell (/bin/sh) (cmd for windows). `execute form` executes directly without spinning up new shell.

- `ENTRYPOINT` - same as `CMD` instruction, but we can always override the default cmd (given in `docker run` cmd ) while starting container. For overriding `ENTRYPOINT`, `--entrypoint` can be used in `docker run` cmd.

## Removing dangling images

- Dangling images are image which lost relation and have been replaced by new images. These images have `<none>` repo and tag.

- To remove such image `docker image prune` is used.

## To remove any image

> `docker image rm <images-name/tag-or-id>:<tag>`

## To remove all stopped containers

> `docker container prune`

## To change tag of image after build

> `docker image tag <image-name>:<tag> <image-name>:<new-tag>`

> For changing latest tag to point to latest version `docker image tag <img-id> <image-name>:latest`.

## To save any image in compressed form

> `docker image save -o <name-of-target-file>.tar <image-name>:<tag>`

## For loading any compressed image

> `docker image load -i <name-of-input-file>`

## Running container in deteched mode (in backgroud)

> `docker run -d <image-name>`

## Running a container with name given to it

> `docker run -d --name blue-sky react-app`

## For logs of running container

> `docker logs <container_id>`. Use `-f` to follow the log. `docker logs -f <container_id>`. use `-n` for last number of lines `docker logs -n 5 <container_id>`. To see timestamps with log use `-t` with the cmd. `docker logs -t <container_id>`

## Publishing the ports (mapping to local machine)

> `docker run -d -p <port-of-localmachine>:<port-of-container> <imagename>`

## Execute cmds in running containers

> `docker exec <container-id/name> <cmd>`

## Remove a container

> `docker container rm <containername/id>` or `docker rm <containername/id>`. To force remove, use `-f` in cmd.

## Creating a volume for container

> `docker volume create <volume-name>`

## Run docker container with mapped volume

> `docker run -d -p 3000:3000 -v <local-volume>:<dir-of-container> <image-name>`

## Copy file from container to host

> `docker cp <container_id>:<path-to-file> <target-dir-.-for-currentdir>`

## Copy file from host to container

> `docker cp <target-dir-.-for-currentdir> <container_id>:<path-to-file>`

## Sharing source code with working dir of container in order to make changes in dev mode

For linux/mac

> `docker run -d -p <host-port>:<container-port> -v $(pwd):<dir-in-container> <image-name>`

For Power shell

> `docker run -d -p <host-port>:<container-port> -v ${PWD}:<dir-in-container> <image-name>`

## List all images with id

> `docker image ls -q`

## Remove all images in one go

> `docker image rm $(docker image ls -q)`

## List all containers with id

> `docker container ls -q`

## Remove all containers in one go

> `docker container rm -f $(docker container ls -a -q)` or `-aq`