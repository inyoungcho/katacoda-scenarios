Providing containers access to the host namespace is sometimes required, such as for debugging tooling, but is generally regarded as bad practice. This is because you're breaking out of the container security model which may introduce vulnerabilities. Instead, if it's required, use a shared namespace to provide access to only the namespaces the container requires.

## Example

The first container starts an nginx server. This will define a new network and process namespace. The nginx server will bind itself to port 80 of the newly defined network interface.

`docker run -d --name http nginx:alpine`{{execute}}

Other containers can now reuse this namespace using the syntax _container:&lt;name&gt;_. Below the curl command can access the HTTP server running on localhost because they share the same network interface.

`docker run --net=container:http benhall/curl curl -s localhost`{{execute}}

It can also see and interface with the processes in the shared container.

`docker run --pid=container:http alpine ps aux`{{execute}}

This is useful for debugging tools, such as strace. This allows you to give more permissions to certain containers without changing or restarting the application. 
