# Docker

# Docker
## What is Docker?
**Docker is a platform that helps build containers.** It separates the applications from the underlying infrastructure and helps reduce the time of the build, ship, test, and deploy life cycle.

### Reddit Explanation of Docker / Containerized Applications
![What is Docker - Reddit Explanation](https://i.imgur.com/pUrjDeL.png)

## Docker Architecture
![Docker Architecture Digram](https://i.imgur.com/IUvgj43.png)  
A client communicates with the Docker daemon (that can be on the same system or on a remote system). The daemon does the heavy lifting of building, running, and distributing your Docker containers.  

## Docker Daemon (dockerd)
Listens for Docker API requests and is responsible for managing Docker objects (images, containers, volumes, etc).
## Docker Client (docker)
Sends Docker API requests.  
  
### Example of `docker run` command:
```
 docker run -i -t ubuntu /bin/bash
``` 
The following command runs an `ubuntu` container, attaches interactively to your local command-line session, and runs /bin/bash.\

## How Docker Builds Container Images
Docker container images are built using a Dockerfile. Docker is built on this idea of layers which are cached and reused if no modifications were made -- making operations like image rebuild super efficient.

![Docker layer diagram](https://i.imgur.com/4EJEuxI.png)
# Resources Utilized
* [Docker Overview](https://docs.docker.com/get-started/overview/)  