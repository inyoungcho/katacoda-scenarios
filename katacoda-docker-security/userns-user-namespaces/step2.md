This risk can be migrated by changing the user and group context and the container running as an unprivileged user.

`docker run --user=1000:1000 --rm alpine id`{{execute}}

As a unprivileged user, it would not be possible to delete the binary.

`sudo cp /bin/touch /bin/touch.bak
docker run --user=1000:1000 -it -v /bin:/host/ alpine rm -f /host/touch.bak`{{execute}}

However, if we required root level access inside the container, then we still expose ourselves to the previous scenario. This is where user namespaces come in.
