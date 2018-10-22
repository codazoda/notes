# Docker Cheat Sheet

List local images.

`docker images`

List running containers.

`docker ps`

List all containers.

`docker ps -a`

Start the container if it's not already started.

`docker start [name]`

Stop a running container.

`docker stop [name]`

Attach a TTY to a docker container.

`docker attach [name]`

Create a new docker container and start it.

`docker run [image]`

Delete a docker container.

`docker rm [name]`

## Mount a Host Directory to a Container Directory

`docker run -v /host/directory:/container/directory`

`docker run -v ~/Sandbox/:/var/www/ [name]`
