In this step you'll verify that the Docker daemon, and containers, run by default as root. You will also force a single container to run under a different security context.

You must perform this step while logged in as the **ubuntu** user.

## Task

Use the `ps` command to verify that the *Docker daemon* is currently running under the **root** user's security context by running a **command**

`ps aux | grep dockerd`{{execute}}

You see the followings:

   ```
   ubuntu@node:~$ ps aux | grep dockerd

   root      8715  0.0  1.0 352332 38820 ?        Ssl  12:56   0:01 /usr/bin/dockerd -H fd://
   ubuntu    8896  0.0  0.0   8216  2188 pts/0    S+   13:45   0:00 grep --color=auto dockerd

   ```
The first line shows the Docker daemon (**dockerd**). The second line shows the `ps` command you just ran. The first column of the first line shows that the Docker daemon is running as **root**.

## Task

Start a new container that runs the `id` command by running a **command**

`sudo docker run --rm alpine id`{{execute}}

You see the followings:

```
   ubuntu@node:~$ sudo docker run --rm alpine id

   Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
e110a4a17941: Pull complete
Digest: sha256:3dcdb92d7432d56604d4545cbd324b14e647b313626d99b889d0626de158f73a
Status: Downloaded newer image for alpine:latest
uid=0(root) gid=0(root) groups=0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),11(floppy),20(dialout),26(tape),27(video)

   ```
   The last line of the output above shows that the container is running as root - `uid=0(root)` and `gid=0(root)`.

   This step has shown you that the Docker daemon runs as root by default. You have also seen that new containers also start as root.
