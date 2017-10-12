# Docker CheetSheet

### Creates a container of the given image
```
docker run <options> <image_name>
```
#### Most used options
- -p publish a port from the container to your local machine "-p \<host port\>:\<container port\>"
- -e set an environment variable for the container "-e \<VariableName\>=VALUE"
- -v mount a volume from the host to the container "-v /absolut/path/dir:/container/path"
- -d detached mode will put the container to run in the background
- --name set a name for the container
- --rm deletes the container after it has finished the process

### Creates an image from a docker file
```
docker build <options> <path to directory>
```
#### Options
- -t set the tag for the builed image

### Container management
```
docker ps
```
List all the running containers
```
docker ps -a
```
List all the containers even the stopped ones
```
docker start <container name or container id>
docker stop  <container name or container id>
docker rm <container name or container id>
```
Start stop and remove containers

### Manage Images
```
docker image ls
```
List all the images on your computer
```
docker image rm <image name>
```
remove an image from yout system usually to clean some space
```
docker exec -it <container Name> <command>
```
executes a command inside a container usually run bash

### Sharing the image

save an image into a file
```
docker save <image name> > name.tar.gz
```
load an image from a file
```
docker load < name.tar.gz
```
```
docker push <image name>
```
to push to the public repository you should prefix your image with your username like adalessa/imagename:version
for a local repository preapend the image with the server url


## Docker compose

```
docker-compose up
```
Get the configuration running, add the -d to run detached
```
docker-compose ps
```
List the running services for the configuration
```
docker-compose down
```
Stop and destroy the containers
```
docker-compose restart
```
stop and start all the services
```
docker-compose exec <service Name> <command>
```
execute a command inside a services
