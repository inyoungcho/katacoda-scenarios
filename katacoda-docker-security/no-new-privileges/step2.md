Create Dockerfile:
`
echo 'FROM benhall/strace-ubuntu:latest' >> 2_Dockerfile
echo 'ADD 2_setuid /setuid' >> 2_Dockerfile
echo 'ADD 2_suid.sh /tmp/suid.sh' >> 2_Dockerfile
echo 'RUN chmod u+s /setuid /tmp/suid.sh' >> 2_Dockerfile
echo 'CMD ["/setuid"]' >> 2_Dockerfile
`{{execute}}

Download Command:
`curl -LO https://github.com/katacoda/oscon2016-docker-perf-sec/raw/master/tutorial/2_Security/3_no-new-privileges/2_setuid && chmod +x 2_setuid`{{execute}}

`curl -LO https://github.com/katacoda/oscon2016-docker-perf-sec/raw/master/tutorial/2_Security/3_no-new-privileges/2_suid.sh && chmod +x 2_suid.sh`{{execute}}

Build:
`docker build -f 2_Dockerfile -t new-priv-2 .`{{execute}}

Run:
`docker run -u 1000 new-priv-2`{{execute}}

Is that the output you expected? How could you secure the user gaining root access?
