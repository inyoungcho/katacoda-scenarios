SecComp is a very low level protocol. In order to block syscalls you first need to identify which calls are being made.

_strace_ is also used to identify the underlying syscall being made by the operating system. While the shell command is called _chmod_, the underlying system call could be different.

If we take our profile and apply it to Ubuntu, the command will work.

`docker run --rm -it \
  --cap-add SYS_PTRACE \
  --security-opt seccomp:1_chmod.json \
  benhall/strace-ubuntu \
  chmod 400 / && 
  echo $?`{{execute}}

This is because Ubuntu is using a different syscall under the covers. We need to use _strace_ to update the syscall restrictions but first we need to identify the correct name. The _strace_ commands will output every syscall made by a process. We can use this to identify calls we need to allow / disallow.

Below there are two containers, one based on Ubuntu and one based on Alpine. Run strace and identify which syscalls are being made by each container.

## strace on Ubuntu
`docker run --rm -it \
  --cap-add SYS_PTRACE \
  --security-opt seccomp:1_chmod.json \
  benhall/strace-ubuntu \
  strace chmod 400 /`{{execute}}

When is chmod executed? Is it successful?

## strace on Apline

`docker run --rm -it \
  --cap-add SYS_PTRACE \
  --security-opt seccomp:1_chmod.json \
  benhall/strace \
  strace chmod 400 /`{{execute}}

Why is Alpine different?
