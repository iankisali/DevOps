## Commands executed on ubuntu server to setup Nexus

### Installing Java version 8
- `apt update`
- `apt install openjdk-8-jre-headless`
- `apt install net-tools`

### Setting up and downloading Nexus package
- `cd /opt`

- `wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz`

### Untaring Nexus package
- `tar -zxvf latest-unix.tar.gz`

### Creating Nexus user
- `adduser nexus`

### Giving user permissions
- `chown -R nexus:nexus nexus-3.28.1-01`
- `chown -R nexus:nexus sonatype-work`

### Setting up to run Nexus with Nexus user
- `vim nexus-3.28.1-01/bin/nexus.rc`

- run_as_user="nexus"

### Switching to Nexus user
- `su - nexus`

### Starting Nexus
- `/opt/nexus-3.28.1-01/bin/nexus start`

### Commands to check Nexus is running correctly
- `ps aux | grep nexus`

- `netstat -lnpt`


## Running Nexus as Docker Container in Ubuntu

### Updating Ubuntu and dowloading Docker
- `sudo apt update`

### Persistent Data using Docker volumes - Named Volume

- `docker volume create --name nexus-data`

- `docker run -d -p 8081:8081 --name nexus -v nexus-data:/nexus-data sonatype/nexus3`