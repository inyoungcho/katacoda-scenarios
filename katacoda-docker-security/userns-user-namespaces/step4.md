With userns enabled, the Docker Dameon will be running as a different user.

`ps aux | grep dockerd`{{execute}}

When containers are launched, the user inside the container will have root privileges.

`docker run --rm alpine id`{{execute}}

However, the user will not be able to modify anything running on the host.

`sudo cp /bin/touch /bin/touch.bak
docker run -it -v /bin/:/host/ alpine rm -f /host/touch.bak`{{execute}}

Unlike before, our ps command still exists.

`ls -lha /bin/touch.bak`{{execute}}

By using User Namespaces, it's possible to separate Docker root users and provide more security and isolation than previously available.
