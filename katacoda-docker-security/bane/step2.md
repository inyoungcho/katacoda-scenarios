"Reviewing AppArmor profile pull requests is the bane of my existence" Jess Frazelle

Download Bane:
`
sudo curl -L http://assets.joinscrapbook.com/bane -o /usr/local/bin/bane
sudo chmod +x /usr/local/bin/bane`{{execute}}

Download Sample:
`curl -LO https://raw.githubusercontent.com/jessfraz/bane/master/sample.toml`{{execute}}

View Sample:
`cat sample.toml`{{execute}}

Generate and Install Profile:
`sudo bane sample.toml`{{execute}}

Start Container:
`docker run -d --security-opt="apparmor:docker-nginx-sample" -p 80:80 --name nginx nginx:1.9`{{execute}}

Execute Into Container:
`docker exec -it nginx bash`{{execute}}

Try the following commands:
<pre>
ping 8.8.8.8
top
touch ~/thing
sh
dash
</pre>
