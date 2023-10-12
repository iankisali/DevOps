### Starting up Jenkins as a Docker container
`docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts`

### create jenkins container with mounted docker -> Command to start a new container with necessary volume
`docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home -v/var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker jenkins/jenkins:lts`

### Entering as root user to modify docker.sock permission
`docker exec -u 0 -it 0c73a1692b75 bash`
`chmod 666 /var/run/docker.sock`

### Pushing an image to private DockerHub repo
`docker build -t iankisali/demo-repo:jma-1.0 .`
`docker login -u $USERNAME -p $PASSWORD` == `echo $PASSWORD | docker login -u $USERNAME --password-stdin` (safest method)
`docker push iankisali/demo-repo:jma-1.0`

### Pushing an image to Nexus repo
`docker build -t 51.20.124.248:8083/java-maven-app:1.0 .`
`echo $PASSWORD | docker login -u $USERNAME --password-stdin 51.20.124.248:8083`
`docker push 51.20.124.248:8083/java-maven-app:1.0`

### Editing or creating /etc/docker/daemon.json on HOST 
`vim /etc/docker/daemon.json`
`{
	"insecure-registries" : ["167.99.248.163:8083"]
}`

### restarting docker
`systemctl restart docker`

### enter as root and modify docker.sock permission
`docker exec -u 0 -it 0c73a1692b75 bash`
`chmod 666 /var/run/docker.run`

