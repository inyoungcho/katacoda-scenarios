While memory limits defined a set maximum, CPU limits are based on shares. These shares are a weight between how much processing time one process should get compared to another. If a CPU is idle, then the process will use all the available resources. If a second process requires the CPU then the available CPU time will be shared based on the weighting.

## Example

Below is an example of starting a container with different shares. The `--cpu-shares` parameter defines a share between 0-1024. If a container defines a share of 1024, while another defines a share of 512, the first container will have 50% share with the other having 25% of the available share total.

Below the first container will be allowed to have 75% of the share. The second container will be limited to 25%.

```
docker run -d --name c768 --cpuset-cpus 0 --cpu-shares 768 benhall/stress
docker run -d --name c256 --cpuset-cpus 0 --cpu-shares 256 benhall/stress
sleep 5
docker stats --no-stream
docker rm -f c768 c256
```{{execute}}

It's important to note that a process can have 100% of the share, no matter defined weight, if no other processes is running.
