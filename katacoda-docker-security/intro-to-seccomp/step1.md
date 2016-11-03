## Permissions
SecComp defines which system calls should and should not be allowed to be executed by a container. They're defined in a JSON file that is applied when a container starts. In this initial step we've defined seccomp permissions to disable allowing containers to run seccomp.

`cat 1_chmod.json`{{execute}}


## Applying Restrictions to Containers

Launch a container and try to run chmod.

`docker run --rm -it \
  --security-opt seccomp:1_chmod.json \
  benhall/strace \
  chmod 400 /etc/hostname`{{execute}}

Because our container attempted to execute chmod, the call failed with _Operation not permitted_. This is because our seccomp profile blocked it.

We can extend our seccomp profile to list all the calls we want to allow or disallow. This allows us to block potential attack vectors or close vulnerabilities without changing our application. 
