# [Docker](https://docs.docker.com/reference/)


### Downloading an image from image registry. Most images obtained from Docker Hub registry.
- ```docker pull <image-name>```

### Pulling image and starting container
- ```docker run <container-name>``` 

Important note:

- ```docker run = docker pull + docker start```

### Pulling image and starting container in detach mode
- ```docker run -d <container-name>```

### Pulling image, starting container in detach mode and binding host port number 8080 to container port 80

- ```docker run -p8080:80 -d <container-name>```

### Pulling image, starting container in detach mode and binding host port number 8080 to container port 80 and providing preferred container name.

- ```docker run -p8080:80 -d <container-name> --name <preferred-container-name>```

### Command to obtain images already downloaded locally.
- ```docker images```

### Listing containers running on host.

- ```docker ps```

### Viewing a list of all containers including containers stopped.

- ```docker ps -a (all)```

### Restarting a stopped container with previous changes in place. 

- ```docker start <container-id>```

### Stopping a running container.

- ```docker stop <container-id>```


## Troubleshooting

### Retrieves log messages at container
- ```docker container logs [OPTIONS] <container-id/container-name>```

### Retrieves log messages of a service running on container

- ```docker service logs [OPTIONS] <container-id/container-name>```

### Getting into container shell(interactive terminal) using bash. Same as SSHing into a running container.

- ```docker exec -it(interactive terminal) <container-id> /bin/bash ```

### Listing available docker networks

- ```docker network ls```

### Creating docker network called mongo-network. Network enabled linking container to many networks.

- ```docker network create mongo-network```