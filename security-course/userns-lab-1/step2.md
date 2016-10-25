User namespaces have been part of the Linux kernel for a while. They have been available in Docker since version 1.10 of the Linux Docker Engine. They allow the Docker daemon to create an isolated namespace that looks and feels like a root namespace. However, the `root` user inside of this namespace is mapped to a non-privileged **uid** on the Docker Host. This means that containers can effectively have root privilege inside of the user namespace, but have no privileges on the Docker Host.

In this step you'll see how to implement user namespaces.

> **Note:** It is not recommended to switch the Docker daemon back and forth between having user namespace mode enabled, and user namespace mode disabled. Doing this can cause issues with image permissions and visibility.

## Task

Stop the Docker Daemon



`sudo systemctl stop docker`{{execute}}



## Task

Start the Docker Daemon with user namespace support enabled.



`sudo dockerd --userns-remap=default &`{{execute}}

If you are using a Docker 1.11 or earlier you will need to supplement `dockerd` with `docker daemon` in the previous command.

  This will start the Docker Daemon in the background using the default user namespace mapping where the **dockermap** user and group are created and mapped to non-privileged **uid** and **gid** ranges in the `/etc/subuid` and `/etc/subgid` files.

  The `/etc/subuid` and `/etc/subgid` files have a single-line entry for each user/group. Each line is formatted with three fields as follows -

  - User or group name
  - Subordinate user ID (uid) or group ID (gid)
  - Number of subordinate ID's available
