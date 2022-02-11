# Section 5: Docker Containers Management (Ubuntu, NGINX)


## Running container in background -d

```bash
# in a browser, every time you refresh in the terminal will register the action
$  docker run -p 8080:80 nginx

# -d : it running in background -d, it will give you a CONTAINER ID
$  docker run -p 8080:80 -d nginx
$ docker logs [CONTAINER ID]

# -f: persist logs in terminal

$ docker logs [CONTAINER ID] -f
```

## Running container with Pseudo TTY

> in `docker run --help`, you can identify -i and -t which are used to excecute in iterative mode

```console
-i, --interactive                    Keep STDIN open even if not attached
    --ip string                      IPv4 address (e.g., 172.30.100104)
    --ip6 string                     IPv6 address (e.g., 2001:db8::33)
    --ipc string                     IPC mode to use
    --isolation string               Container isolation technology
    --kernel-memory bytes            Kernel memory limit
.
.
.
 -t, --tty                            Allocate a pseudo-TTY

```

# -i
```bash
# it permites to enter any commands inside container
$ docker run -i alpine 
# inside container
$ exit
```


# -t
```bash
# it doesn't permites to enter commands inside container
$ docker run -t alpine 
# inside container
$ exit
```

# -it or -i -t 
```bash
$ docker run -it alpine 
# inside container
$ exit
```

## Remove container and prune containers

```bash
# remove a specific container with name or container id, use flag -f to force deleting
$ docker rm [CONTAINER ID] or [NAME]
# Remove all stopped containers
$ docker container prune
```


 