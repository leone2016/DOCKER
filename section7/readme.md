# Section 7: Running Node.js Applications in Docker


## Running nodeJs container

```bash
# download image 
$ docker pull node

#  run image and exit immediately
$ docker run node

$ docker run -it node

### -> inside node contaider, you can see .exit

>>> .help
>>> console.log("Hello from Node.js container")
>>> .exit
```

## Hello world application with node

```bash
# inside the folder node
# first node means container
# second node means command
$ docker run -v $PWD:/app node node /app/hello.js

# relative flder node 
$ docker run -v /home/leonardo/docker_data/node:/app -w /app node node hello.js
# alternative
$ docker run -v /home/leonardo/docker_data/node:/app node node /app/hello.js

```

## Express web server using Node

```bash
# 1st init a npm project, here docker will be create a file inside docker and local computer (inside express folder)
$ docker run -v /home/leonardo/docker_data/node/express:/app -w /app -it node npm init

# 2nd  install express, inside local folder you could see a node_modules folder (inside express folder)
$ docker run -v /home/leonardo/docker_data/node/express:/app -w /app -it node npm install express

# 3th  run index.js server, here the servers is UP, dash p (-p [internalPort]:[externalPort]) is for use the same external port (inside express folder)
$ docker run -v /home/leonardo/docker_data/node/express:/app -w /app -it node npm install  


# execute application

$ docker run -v /home/leonardo/docker_data/node/express:/app -w /app -it -p 3000:3000 node node index.js

# kill server
$ docker kill [CONTAINER ID]
```

## Add handling of the SIGINT and SIGTERM signals

> inside express/index.js there are 2 signals SIGINT and SIGTERM

* **SIGINT**: cuando se utiliza ctrl + c, la aplicacion se interumpe y se muestra en pantalla la siguiente informacion 
`Application is being interrupted`
* **SIGTERM**: when execute `docker stop CONTAINER_ID`
`Application is being terminated`


## CHALLENGE

Create Node.js application that will:
1. Ask in the terminal for filename
2. Ask for some text
3. Create file with supplied filename
like <filename>.txt with text
contents supplied at the previous
step


```bash
# create folder
$ mkdir /home/leonardo/docker_data/node/files
$ touch index.js

$ docker run -v /home/leonardo/docker_data/node/files:/app -w /app -it node node index.js
```