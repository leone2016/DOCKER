# Section 6: Running Python Applications in Docker


```bash
# download image 
$ docker pull python

# run image and exit immediately
$ docker run python

# run and still alive
$ docker run -it python

## Inside python container
>>> exit()
```

## Simple python program

```bash
# keep in mind, this file /app/hello.py is inside the python container, reference with volume
$ docker run -it -v /home/leonardo/docker_data/python/:/app python python3 /app/hello.py

# alternative comand
$ docker run -it -v /home/leonardo/docker_data/python/:/app -w /app python python3  hello.py

```

### Calendar application
```bash
$ docker run -it -v /home/leonardo/docker_data/python/:/app python python3 /app/calendario.py
```