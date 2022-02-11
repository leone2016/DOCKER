# Section 8: Running MongoDB Containers


```bash
# download image 
$ docker pull mongo

# this command will connect with mongo dprocess, for this reason we need to run additional process inside the running container
$ docker run mongo

# How could we start additional process in the running container?
```


## Starting additional process inside the runnig container

> in `docker help` we can find mode information additional commands like `exec       Run a command in a running container
`

```bash

$ docker run mongo

CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS       NAMES
f1606514441a   mongo     "docker-entrypoint.s…"   6 seconds ago   Up 5 seconds   27017/tcp   lucid_wescoff
# running a command inside running container
## important -it, without this the command execute and exit inmediatly
### docker exec -it [CONTAINER ID] bash 
$ docker exec -it f1606514441a bash 

### INSIDE BASH PROCESS - MONGO

root@f1606514441a:/# ls
bin   data  docker-entrypoint-initdb.d  home        lib    lib64   media  opt   root  sbin  sys  usr
boot  dev   etc                         js-yaml.js  lib32  libx32  mnt    proc  run   srv   tmp  var
#process executed
root@f1606514441a:/# ps -e

```

## What is entry point and where is it located

```bash
# docker inspect [CONTAINER ID]
# this will give us the details about runnign container
$ docker inspect f1606514441a

## this command - inspect - how to mongo container was created
#  "Path": "docker-entrypoint.sh", to create this container was used this script .sh and there was arguments Args: [ mongod ] that were passed to this script   
[
    {
        "Id": "f1606514441a9b8f78d9aa83938b4f9119e9a5e3f270d48faa84a1b9c183b8dd",
        "Created": "2022-02-11T16:23:37.573972322Z",
        "Path": "docker-entrypoint.sh",
        "Args": [
            "mongod"
        ],
        .
        .
        .
        .

```


> search `"Path": "docker-entrypoint.sh"` inside mongo container

```bash
## docker exec -it [  ID] bash
$ docker exec -it f1606514441a bash
## inside mongo container 
root@f1606514441a:/# ls /usr/local/bin
docker-entrypoint.sh  gosu
```

## Creating new Mongo Database using mogo shell

```bash
## docker exec -it [  ID] mongo
## enter inside mongo shell
$ docker exec -it f1606514441a mongo

## inside mongo shell 
> show dbs
> db.version()

> use test
switched to db test
>db
test

> db.animals.insert({ "animal": "cat" })
WriteResult({ "nInserted" : 1 })

> db.animals.find()
{ "_id" : ObjectId("6206a033a1cb090c6cc0c97a"), "animal" : "cat" }

```

 CONCLUSION
>This new mongo container has
new empty database
It doesn't have access to the database of
the previous continer

## Running Mongo container with persistent database

```bash

$ docker run -d -v /home/leonardo/docker_data/mongo/db:/data/db mongo 

## Open mongo shel
docker exec -it ee9623fd1ed5 mongo

```

```bash
>show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
> use mydb
> db.posts.insert({ "post": "hey there" })
WriteResult({ "nInserted" : 1 })
> db.posts.insert({ "post": "how are you?" })
WriteResult({ "nInserted" : 1 })
> db.posts.insert({ "post": "Doing well" })
WriteResult({ "nInserted" : 1 })
> db.posts.find()
{ "_id" : ObjectId("6206c00b06c4412bf8d13bc0"), "post" : "hey there" }
{ "_id" : ObjectId("6206c02906c4412bf8d13bc1"), "post" : "how are you?" }
{ "_id" : ObjectId("6206c03106c4412bf8d13bc2"), "post" : "Doing well" }
> 
```