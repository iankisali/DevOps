### Starting up Jenkins as a Docker container
`docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts`

### create jenkins container with mounted docker -> Command to start a new container with necessary volume
`docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home -v/var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker jenkins/jenkins:lts`