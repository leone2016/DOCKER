

### There are 4 Chapters in the course:

* CHAPTER 1: Practice - running different kinds of containers using Docker
* CHAPTER 2: Diagrams - Docker Concepts
* CHAPTER 3: Linux Fundamentals
* CHAPTER 4: Course project - Dockerfiles and Docker Compose



### List of the introductory practical sections for beginners:

* Section 2: Docker Installation
* Section 3: Basic Docker Containers (Ubuntu, Busybox, Alpine)
* Section 4: Port and Volume Mapping in the Docker Containers
* Section 5: Docker Containers Management (Ubuntu, NGINX)
* Section 6: Running Python Applications in Docker
* Section 7: Running Node.js Applications in Docker
* Section 8: Running MongoDB Containers
* Section 9: Communication between Containers and Environment Variables (MySQL, phpMyAdmin)
* Section 10: Default and Custom Bridge Networks in Docker (Wordpress, MySQL)
* Section 11: Additional Containers - Elasticsearch, Redis, Httpd

```bash
# delete all images
$ docker rmi -f $(docker images -aq)

# delete all containers
$ docker rm -vf $(docker ps -aq)
```


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
