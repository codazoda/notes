# Docker Cheat Sheet

## Create Debian 7 Wheezy Container

`docker create -it --name [name] debian:wheezy`

## List all Local Containers

`docker ps -a`

## List Running Containers

`docker ps`

## Start and Attach to a Container

Start the container if it's not already started.

`docker start [name]`

Then attach to it.

`docker attach [name]`

## Mount a Host Directory to a Container Directory

`docker run -v /host/directory:/container/directory`

`docker run -v ~/Sandbox/:/var/www/ [name]`
