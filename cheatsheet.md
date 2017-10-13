# Docker Cheatsheet

- Cheatsheet url: https://goo.gl/T8SJKk
- Slides url: https://goo.gl/NkzpEY

### Creates a container of the given image
```
docker run [options] image_name [command]
```
#### Most used options
You can get this list and more by running `docker run --help`.

- `-p` or `--publish` publish a port from the container to your local machine "-p \<host port\>:\<container port\>"
- `-v` or `--volume` mount a volume from the host to the container "-v /absolut/path/dir:/container/path"
- `-e` or `--env` set an environment variable for the container "-e \<VariableName\>=VALUE"
- `-i` or `--interactive` keep STDIN open even if not attached
- `-t` or `--tty` allocate a pseudo-TTY
- `-d` or `--detach` detached mode will put the container to run in the background
- `--rm` deletes the container after it has finished the process
- `--name` set a name for the container

#### Examples

Start nginx server
```
docker run --publish 8080:80 --volume /some/content:/usr/share/nginx/html nginx
```

Start mysql server
```
docker run --publish 3306:3306 --name some-mysql -e MYSQL_ROOT_PASSWORD=root -d mysql
```

Start bash in a fresh Ubuntu
```
docker run -it ubuntu bash
```

### Creates an image from a docker file

```
docker build <options> <path to directory>
```

#### Options

- `-t` set the tag for the builed image

### Container management

List all the running containers

```
docker ps
```

List all the containers even the stopped ones

```
docker ps -a
```

Start stop and remove containers

```
docker start <container name or container id>
docker stop  <container name or container id>
docker rm <container name or container id>
```


### Manage Images

List all the images on your computer

```
docker image ls
```

Remove an image from yout system usually to clean some space

```
docker image rm <image name>
```

Executes a command inside a container usually run bash

```
docker exec -it <container Name> <command>
```


### Sharing the image

save an image into a file

```
docker save <image name> > name.tar.gz
```

load an image from a file

```
docker load < name.tar.gz
```

To push to the public repository you should prefix your image with your username like adalessa/imagename:version
for a local repository preapend the image with the server url

```
docker push <image name>
```

## Docker compose

Get the configuration running, add the -d to run detached

```
docker-compose up
```

List the running services for the configuration

```
docker-compose ps
```

Stop and destroy the containers

```
docker-compose down
```

Stop and start all the services

```
docker-compose restart
```

Execute a command inside a services
```
docker-compose exec <service Name> <command>
```
