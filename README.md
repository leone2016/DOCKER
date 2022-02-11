

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
