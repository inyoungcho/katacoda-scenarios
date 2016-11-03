
## Download AppArmor Nginx Profile

`curl -LO https://raw.githubusercontent.com/katacoda/oscon2016-docker-perf-sec/master/tutorial/2_Security/4_apparmor/docker-nginx`{{execute}}

`cat docker-nginx`{{execute}}


## Parse

`sudo apparmor_parser -r -W docker-nginx`{{execute}}

# run with profile
`docker run --security-opt "apparmor=docker-nginx" -p 80:80 -d --name apparmor-nginx nginx`{{execute}}

Execute Into Container:
`docker exec -it apparmor-nginx bash`{{execute}}

Try the following commands:
<pre>
ping 8.8.8.8
top
touch ~/thing
</pre>
