# Section 4: Port and Volume Mapping in the Docker Containers


##  Running Nginx with exposed port 
> it's a popular web server, scalable and serving content by http or https as protocols, it's posible to use like load balancer and create multiple web servers

```bash
# download LASTEST docker image
$ docker pull nginx

# now we are connected to STDIN and STDOUT of nginx process of the container
$ docker run nginx

```

```sh
# stop process
$ docker stop [CONTAINER ID]
$ docker stop [NAMES]
```
> Waiting 10 seconds...
Please use docker kill instead of docker stop because
sh process doesn't react to the SIGTERM signal that is
sent by docker to the container after "docker stop".
In 10 sec docker stop fallbacks to the docker kill.

> nginx run inside container port 80, we need somehow to open the port on my computer **-p**, this means that actually connected nginx container web server

```sh
# -p [OPEN EXTERNAL PORT] : [ PORT INSIDE CONTAINER]
$  docker run -p 8080:80 nginx

```

## Nginx container with custom content - volumen

create local html file 


```bash
# absolute path folder
$ pwd 

# go ...
cd /home/leonardo/docker_data/nginx
touch index.html
```
```html
<h1>Hello from the custom web page!</h1>
```

```bash

# -v [EXTERNAL PORT]:[INTERNAL PORT] [dockerImage]
$  docker run -p 8081:80 -v /home/leonardo/docker_data/nginx:/usr/share/nginx/html nginx 

# In the folder that contents index.html
$  docker run -p 8081:80 -v $PWD:/usr/share/nginx/html nginx 

# docker logs [idNginx Running]
$ docker logs 
```

