# D O C K E R - BEGINNER

```bash
```
## Running hello-world container

```bash
# Download a docker image called hello-world
$ docker run hello-world
# verify no docker container running
$ docker ps
```

## Running Ubuntu container
```bash
# Download a docker image ubuntu
$ docker run ubuntu
# you'll see if there is a docker running
$ docker ps
# history of docker that were executed 
$ docker ps -a

# to see all images downloaded
$ docker images

# alternative of > docker ps -a
$ docker container ls -a 

#  EXCECUTE ubuntu inside container, after download image - still running
$ docker run -it ubuntu

# inside ubuntu 
> exit
```

## Running Busybox container

```bash
# Download LASTEST docker image, KEEP IN MIND, that busybox is not a full features linux Os
$ docker run busybox
# enter and execute inside container busybox
$ docker run -it busybox
```


> A busy box busy box is a really small distribution that has a really large
set of utilities but also
deal is a custom and they are actually really small in size and usually
this busy box installation is
packaged as a single executable file and let's have a look at the size of
this busy box image in comparison
to a ubuntu to image let's exit this container like so and if l'll list the
containers that are running


```bash
# compare size images
$ docker images
```


## Running Alpine container


```bash
#  download LASTEST docker image
$  docker pull alpine

# EXCECUTE ubuntu inside container, after download image
$ docker run -it alpine
```
> inside alpine container -it

```bash
# show the alpine version
$ cat /etc/os-release

# show the shortcut
$  ls -la bin
```
