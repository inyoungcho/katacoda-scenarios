As with networks, the processes a container can see depends on which namespace it belongs too. By changing the Pid namespace allows a container to interact with processes beyond it's normal scope.

## Example

The first container will run in it's own process namespace. As such the only processes it can access are the ones launched in the container.

`docker run -it alpine ps aux`{{execute}}

By changing the namespace to the host, the container can also see all the other processes running on the system.

`docker run -it --pid=host alpine ps aux`{{execute}}
