Create Dockerfile:
`
echo 'FROM benhall/strace-ubuntu:latest' >> 1_Dockerfile
echo 'ADD 1_testnnp /testnnp' >> 1_Dockerfile
echo 'RUN chmod u+s /testnnp' >> 1_Dockerfile
echo 'CMD ["/testnnp"]' >> 1_Dockerfile
`{{execute}}

Download Command:
`curl -LO https://github.com/katacoda/oscon2016-docker-perf-sec/raw/master/tutorial/2_Security/3_no-new-privileges/1_testnnp && chmod +x 1_testnnp`{{execute}}

Build:
`docker build -f 1_Dockerfile -t new-priv-1 .`{{execute}}

Run:
`docker run -u 1000 new-priv-1`{{execute}}

Is that the output you expected?
