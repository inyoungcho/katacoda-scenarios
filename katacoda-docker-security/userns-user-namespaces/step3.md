**Note:** Docker recommends not to switch the Docker daemon back and forth between having user namespace mode enabled, and user namespace mode disabled. Doing this can cause issues with image permissions and visibility.

User Namespaces are a Linux Kernel security feature. The feature allows a root user inside a namespace, or container, to a unprivileged user id on the Host.

## Task

User namespaces are enabled when the Docker Daemon is started using the parameter _--userns-remap=default_. Run the command below to modify the Docker systemd unit and restart the process.

`sudo sed -i 's/2345/2345 --userns-remap=default/g' /etc/default/docker && sudo service docker restart`{{execute}}

Once restarted, you can verify that user namespaces are in place using the following command

`docker info | grep "Root Dir"`{{execute}}

Docker will no longer store files on disk as the root user. Instead, everything is processed as the mapped user. The _Docker Root Dir_ defines where Docker is storing data for the mapped user.

_Note:_ When enabling this feature on an existing system, Docker Images will be required to be re-downloaded.
