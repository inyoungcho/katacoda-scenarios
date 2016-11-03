What happens when you add _--security-opt=no-new-privileges_ ?

`docker run -u 1000 --security-opt=no-new-privileges new-priv-1`{{execute}}

`docker run -u 1000 --security-opt=no-new-privileges new-priv-2`{{execute}}
