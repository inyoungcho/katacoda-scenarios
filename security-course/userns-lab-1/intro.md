##Lab: User Namespaces

By default, the Docker daemon runs as *root*.
This allows the daemon to create and work with the kernel structures required to start containers.
However, it also presents potential security risks. This lab will walk you through implementing
a more secure configuration utilizing *user namespaces*.

###You will complete the following steps in this lab:

- Step 1 - Daemon and container defaults
- Step 2 - The --user flag
- Step 3 - Enabling user namespaces

### Prerequisites

You will need all of the following to complete this lab:

A Linux-based Docker Host running Docker 1.10 or higher
Root access on the Docker Host
Note: The instructions in this lab are tailored to a Docker Host running Ubuntu 15.10. An open documented issue exists with Ubuntu 16.04 Xenial .
