# D O C K E R - BEGINNER

* [git - repo ](https://github.com/bstashchuk/docker)
* [ALPINE](https://alpinelinux.org/)

## COURSE STRUCTURE

## Currently this course already has 3 CHAPTERS:

* CHAPTER 1 - Docker on Practice
* CHAPTER 2 - Docker Fundamentals
* CHAPTER 3 - Linux Fundamentals

## List of the introductory practical sections for beginners:

* Docker Installation
* Basic Docker Containers (Ubuntu, Busybox, Alpine)
* Port and Volume Mapping in the Docker Containers
* Docker Containers Management (Ubuntu, NGINX)
* Running Python Applications in Docker
* Running Node.js Applications in Docker
* Running MongoDB Containers
* Communication between Containers and Environment Variables (MySQL, phpMyAdmin)
* Default and Custom Bridge Networks in Docker (Wordpress, MySQL
* Additional Containers - Elasticsearch, Redis, Httpd

Happy learning!


### Some commands

command  | Explanation 
------------- | -------------
`> docker run hello-world` | download a docker image called hello-world
`> docker run ubuntu`| 
`> docker images`| to see all images downloaded, **repository - tag - image id - created - size**
`> docker ps`| you'll see if there is a docker running
`> docker ps -a`| history of docker that were executed 
`> docker container ls -a`| alternative of `> docker ps -a`
`> docker run -it ubuntu`| EXCECUTE ubuntu inside container, after download image
`> exit`| inside ubuntu 

###  BusyBox

command  | Explanation 
------------- | -------------
`> docker run busybox` | download LASTEST docker image, KEEP IN MIND, that busybox is not a full features linux Os
 
###  Alpine

command  | Explanation 
------------- | -------------
`> docker pull alpine` | download LASTEST docker image
`> docker run -it alpine`| EXCECUTE ubuntu inside container, after download image
`/ # cat /etc/os-release` | inside alpine, show the alpine version
`/ # ls -la bin` | show the shortcut
`> docker run -i alpine`| run docker in background detached mode4


`docker run -d alpine`
`docker run -d nginx`

###  Nginx 
> it's a popular web server, scalable and serving content by http or https as protocols, its posible to use like load baalancer and create multiple web servers

command  | Explanation 
------------- | -------------
`> docker pull nginx` | download LASTEST docker image
`> docker run nginx` | now we are connected to STDIN and STDOUT og nginx processof the container
`> docker ps`| you'll see if there is a docker running
`> docker stop [idDocker]`| stop process
`> docker run -p 8080:80 nginx` | **-p 8080:80** nginx run inside container port 80, we need somehow to open the port on my computer **-p**, this means that actually connected nginx container web server
`> docker run -p 8081:80 -v [PathLocalComputer]:[pathContainer] [dockerImage]`| docker run -p 8081:80 -v C:\containers\nginx:/usr/share/nginx/html nginx 
`> docker run -p 8080:80 -d nginx` | run docker in background
`> docker logs [idNginx Running]` | 


### Some commands linux

command  | Explanation 
------------- | -------------
`:# hostname -i` | see d=the ip address assigned 
