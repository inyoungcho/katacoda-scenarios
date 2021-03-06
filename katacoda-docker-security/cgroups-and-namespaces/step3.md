While cgroups control how much resources a process can use, Namespaces control what a process and see and access.

## Example

When containers are launched, a network interface is defined and create. This gives the container a unique IP address and interface.

`docker run -it alpine ip addr show`{{execute}}

By changing the namespace to _host_, instead of the container's network being isolated with it's own interface, the process will have access to the host machines network interface.

`docker run -it --net=host alpine ip addr show`{{execute}}

If the process listens on ports, they'll be listened on the host interface and mapped to the container.
