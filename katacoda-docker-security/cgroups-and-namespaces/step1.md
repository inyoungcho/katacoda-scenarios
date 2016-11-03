CGroups control how much resources a process can use. By adding restrictions you can deliver a guaranteed Quality of Service to applications by ensuring they have enough space available. It's also possible protect the system from potentially malicious users or applications aiming to perform Denial of Service (DoS) applications via resource exhaustion. This can also help limit applications from memory leaks or other programming bugs by defining upper boundaries.

## Example

`docker run -d --name mb100 --memory 100m alpine top`{{execute}}

The memory usage ad limits of containers can be identified via the _docker stats_ command.

`docker stats --no-stream`{{execute}}
