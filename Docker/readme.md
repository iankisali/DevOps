# Docker

### Downloading an image from image registry. Most images obtained from Docker Hub registry.
- ```docker pull <imagename>```

###
- ```docker run <container-name>``` - pulls image and start container

###
- ```docker run -d <container-name>```

###
- ```docker run -p8080:80 -d <container-name>```

###
- ```docker run -p8080:80 -d <container-name> --name <preferred-container-name>```

### Command to obtaine images already downloaded.
- ```docker images```

###
- ```docker ps```

###
- ```docker ps -a```

###
- ```docker start```

###
- ```docker stop```

###
- ```docker run -d <container-name>```

###
- ```docker run = docker pull + docker start```



## Troubleshooting

###
- ```docker logs <container-id/container-name>```

###
- ```docker exec -it(interactive terminal) <container-id> /bin/bash ```

###
- ```docker network ls```

###
- ```docker network create mongo-network```