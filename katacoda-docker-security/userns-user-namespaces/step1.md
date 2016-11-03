By default, the Docker Daemon runs as root user on the host. By listing all the processes on the box you can identify which user the Docker Daemon runs as.

`ps aux | grep docker`{{execute}}

As a result of the Daemon running as root, any containers started will have the same security context as the host's root user.

`docker run --rm alpine id`{{execute}}

This has the side-effect that if files owned by the root user are accessible from the container, then can be modified by the running container.

## Task

The following command identifies the risk of running containers as root user. In this case the container is capable of deleting the _ps_ binary from the host.

`sudo cp /bin/touch /bin/touch.bak
docker run -it -v /bin/:/host/ alpine rm -f /host/touch.bak`{{execute}}

As a result, the command no longer exists.

`ls -lha /bin/touch.bak`{{execute}}
