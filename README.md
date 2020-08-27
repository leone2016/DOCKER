# D O C K E R - BEGINNER

> ` docker run --help`
> ` docker --help`
> `docker run -p 8081:80 -v ${PWD}:/usr/share/nginx/html nginx`

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
> NOTE: it's not possible to create container with the **same name** as was assigned (manually or randomly) to any of the running/ stopped containers

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

#### Creating multiple ubuntu container from the same image

command  | Explanation 
------------- | -------------
`> docker run -it ubuntu`| EXCECUTE ubuntu inside container 

#### Clean and stop container

command  | Explanation 
------------- | -------------
`> docker start`| command container will be started exactly with the same configuration as it was running with before exit
`> docker ps -a`| list all the containers that exited like history
`> docker rm [dockerName]`| see how to know the name in the video 20
`> docker container prune`| after see all containers docker ps -a 

### Running Python Application in Docker

command  | Explanation 
------------- | -------------
`> docker pull python`| download image 
`> docker run python`| <- run image and exit inmediatly
`> docker run -it python`| run and still alive
`C:\python`| I had some problems with path in linux the absolute path is ${PWD} but in windos is %cd%
`> C:\python>docker run -it -v %cd%:/app python python3 /app/hello.py` | run a file .py 
`> C:\python>docker run -it -v %cd%:/app  -w /app python python3 hello.py` | run a file .py 

### Running Node.js Application in Docker [S7]
command  | Explanation 
------------- | -------------
`> docker pull node`| download image 
`> docker run node`| <- run image and exit inmediatly
`> docker run -it node`| run and still alive
`> .help`| inside node contaider, you can see .exit
`> docker run -v %cd%:/app -w /app node node hello.js`| for linux terminal use $PWD 
`> docker run -v %cd%:/app -w /app -it node npm init`|  1st init a npm proyect, here docker will be create a file inside docker and local computer (inside express folder)
`> docker run -v %cd%:/app -w /app -it node npm install express`|  2nd  install express, inside local folder you could see a node_modules folder (inside express folder)
`> docker run -v %cd%:/app -w /app -it -p node node index `|  3th  run index.js server, here the servers is UP, dash p (-p [internalPort]:[externalPort]) is for use the same external port (inside express folder)
`> docker ps`|  3th  verify if node is up
`> ... `|  3th  verify in any broser localhost:3000 and see if the server is running
`> docker kill [nameContainer]`|  kill server 
`> docker run -v %cd%:/app -w /app -it node npm install process`|  install express (inside express folder)
'docker run -v %cd%:/app -w /app -it node node index.js `| CHALLENGE
### Some commands linux

command  | Explanation 
------------- | -------------
`:# hostname -i` | see d=the ip address assigned 
