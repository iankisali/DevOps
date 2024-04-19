# Jenkins Docs

### Starting up Jenkins as a Docker container
`docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts`

### Creating jenkins container with mounted volume (named volume)-> Command to start a new container with necessary volume
`docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker jenkins/jenkins:lts`

### Entering as root user to modify docker.sock permission
`docker exec -u 0 -it 0c73a1692b75 bash`
`chmod 666 /var/run/docker.sock`

### Location of Jenkins variables
```http://54.172.193.90:8080/env-vars.html/ ``` 

### Configuring git credentials on a Jenkinsfile
`withCredentials([usernamePassword(credentialsId: 'gitlab-credentials/dockerhub-credentials', passwordVariable: 'PASS', usernameVariable: 'USER')])`<br>

### Increment Application Versioning command - Maven
Versioning is important practice in release of an software. Version exists in different files i.e `build.gradle` for Java-Gradle, `pom.xml` for Java-Maven and `package.json` for Javascript files. <br>
An example of a version is 1.1.5-SNAPSHOT which consists of Major.Minor.Patch and suffix. <br>
- Major: Big, breaking changes, not backward compatible <br>
- Minor: new, backward-compatible changes, API features <br>
- Patch: minor changes, bug fixes, doesn't change API <br>

`mvn build-helper:parse-version versions:set -DnewVersion=\${parsedVersion.majorVersion}.\${parsedVersion.minorVersion}.\${parsedVersion.nextIncrementalVersion} versions:commit`<br>
This will increase patch by 1 value.

### Git commands to push changes from local repo to remote repo
`git config --global user.email "jenkins@example.com`<br>
`git config --global user.name "jenkins`<br>
`git remote set-url origin https://${USER}:${PASS}@gitlab.com/iankisali/java-maven-app.git`<br>
`git add .`<br>
`git commit -m "ci: version bump"`<br>
`git push origin HEAD:branch-name`<br>

### Pushing an image to private DockerHub repo
`docker build -t iankisali/demo-repo:jma-1.0 .`<br>
`docker login -u $USERNAME -p $PASSWORD` or <br>
`echo $PASSWORD | docker login -u $USERNAME --password-stdin` (safest method) <br>
`docker push iankisali/demo-repo:jma-1.0`

### Pushing an image to Nexus repo
`docker build -t 51.20.124.248:8083/java-maven-app:1.0 .`<br>
`echo $PASSWORD | docker login -u $USERNAME --password-stdin 51.20.124.248:8083`<br>
`docker push 51.20.124.248:8083/java-maven-app:1.0`<br>

### Editing or creating /etc/docker/daemon.json on HOST 
`vim /etc/docker/daemon.json`<br>
```
{
	"insecure-registries" : ["167.99.248.163:8083"]
}
```

### restarting docker
`systemctl restart docker`

### Entering as root and modify docker.sock permission
`docker exec -u 0 -it 0c73a1692b75 bash` <br>
`chmod 666 /var/run/docker.run`
