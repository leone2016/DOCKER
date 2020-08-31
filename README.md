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
`> docker run python`| <- run image and exit immediately
`> docker run -it python`| run and still alive
`C:\python`| I had some problems with path in linux the absolute path is ${PWD} but in windows is %cd%
`> C:\python>docker run -it -v %cd%:/app python python3 /app/hello.py` | run a file .py 
`> C:\python>docker run -it -v %cd%:/app  -w /app python python3 hello.py` | run a file .py 

### Running Node.js Application in Docker [S7]

command  | Explanation 
------------- | -------------
`> docker pull node`| download image 
`> docker run node`| <- run image and exit immediately
`> docker run -it node`| run and still alive
`> .help`| inside node contaider, you can see .exit
`> docker run -v %cd%:/app -w /app node node hello.js`| for linux terminal use $PWD 
`> docker run -v %cd%:/app -w /app -it node npm init`|  1st init a npm project, here docker will be create a file inside docker and local computer (inside express folder)
`> docker run -v %cd%:/app -w /app -it node npm install express`|  2nd  install express, inside local folder you could see a node_modules folder (inside express folder)
`> docker run -v %cd%:/app -w /app -it -p node node index `|  3th  run index.js server, here the servers is UP, dash p (-p [internalPort]:[externalPort]) is for use the same external port (inside express folder)
`> docker ps`|  3th  verify if node is up
`> ... `|  3th  verify in any broser localhost:3000 and see if the server is running
`> docker kill [nameContainer]`|  kill server 
`> docker run -v %cd%:/app -w /app -it node npm install process`|  install express (inside express folder)
`docker run -v %cd%:/app -w /app -it node node index.js `| CHALLENGE
`docker container prune`| stop all containers

### Running MONGO Application in Docker [S8]

> here I have a important note, we can run a additional process inside of the run container

command  | Explanation 
------------- | -------------
`> docker pull mongo`| download image 
`> docker help`| see more options that we can run, In this case I'll use exec (<-)
`> docker pull mongo`| download image 
`> docker run mongo`| this execute a container with this id **72f80e5cb0b2** 
`> docker exec [idDocker] or [nameDocker]`| download image, to see idDocker or nameDocker, `docker ps`
`> docker exec -it 72 bash`| same above, in the terminal I could see that I'm inside docker container that I enter 
`root@72f80e5cb0b2:/# ps -e`|  list all the processor that are running inside the container, the most important here is to look that we have able to run multiple process inside container
`> docker exec -it 72 sh`| open new shell, after running this command return to bash shell (above), and execute again and look a new process is running 
`> docker inspect [idDocker] or [nameDocker]`| download image 
`root@72f80e5cb0b2:/# ls /use/bin`| here we could find a mongo file that there are executable
`> docker exec -it 72 mongo` | this tell us that actually connected to mongo DB  process from mongo shell and here we are able to perform some actions, for eg. we are able to find out a version of this mongo database  
**INSIDE MONGO SHELL**| ** -- **
`> db.version()` | ***inside mongo shell*
`> show dbs` | **inside mongo shell**
`> use animalsDB` | create a new new database
`> db.animal.insert({"animal": "cat"})` | insert a new collection
`> db.animal.insert({"animal": "dog"})` | insert a new collection
`> db.animal.find()` | list all animals
`> exit` | ...
`> ` | **IMPORTANT** keep in mind, if we repeat all this steps we'll created a new container and inside there are't the database that I created (animalsDB)
`> docker ps -a` | se the last containers 
`> docker start 72` | this start mongo shell
`> docker exec -it 72 mongo` | this execute a container with this id **72f80e5cb0b2**, and here it's possible to see the previous database called animalsDB

#### Running MONGO container with persistence database

command  | Explanation 
------------- | -------------
`> docker run -d -v %cd%/db:/data/db mongo`| -d: Running docker in background, inside folder mongo
`> docker ps -a`| see the container is running, and catch the container id (13f244503833 )
`> docker exec -it 13 bash`| ERROR ..... review class 36 again

### Running WORDPRESS Application in Docker [S9]

command  | Explanation 
------------- | -------------
`> docker pull wordpress`| download image 
`> docker run wordpress`| run image 
`> docker run wordpress`| run image 
`> docker run -d -p 8080:80 wordpress`| run image in background and with diferent port on localhost

#### Running COMUNICATION between containers [S9]

command  | Explanation 
------------- | -------------
`> docker run -it busybox` | enable two containers
`# hostname -i` | see the ip address 
`# env` | download image 
`> docker exec [idContainer] env` | list all environment variables created  
`> docker run mysql` | download and try to run
`> docker run -e [NAME_VARIABLE]=something [nameImage]` |set a environment variable ex: `> docker run -e MYSQL_ROOT_PASSWORD=my-password  mysql`
`> docker exec [idContainer] env` | list all environment variables created 
`> docker pull phpmyadmin/phpmyadmin` | list all environment variables created 


#### Running COMUNICATION between phpMyAdmin and Mysql [S9]
`> docker run -e [NAME_VARIABLE]=something [nameImage]` |set a environment variable ex: `> docker run -e MYSQL_ROOT_PASSWORD=my-password  mysql`
`> docker ps` | se de container id assigned 02b9a9d98484
`> docker exec -it 02 sh` | se de container id assigned 02b9a9d98484 mysql
`# hostname -i` | notice the ip address 172.17.0.2   mysql
`> docker run -p 8080:80 -e PMA_HOST=172.17.0.2 phpmyadmin/phpmyadmin` | connect phpMyAdmin with env with the ip address assigned


# Some linux commands 

command  | Explanation 
------------- | -------------
`:# hostname -i` | see the ip address assigned, the important here is "Path": and "Args": both are in the beginning shell
`:# env` | list all environment variables created
