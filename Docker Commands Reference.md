# Docker Commands Reference

Complete guide to Docker commands for containerization and DevOps.

---

## Images
- `docker images` - List all local images
- `docker pull <image>` - Download image from registry
- `docker build -t <name>:<tag> .` - Build image from Dockerfile
- `docker rmi <image>` - Remove image
- `docker tag <image> <new-name>:<tag>` - Tag an image
- `docker history <image>` - Show image layers

## Containers
- `docker ps` - List running containers
- `docker ps -a` - List all containers (including stopped)
- `docker run <image>` - Create and start container
- `docker run -d <image>` - Run container in detached mode
- `docker run -p 8080:80 <image>` - Map port host:container
- `docker run -v /host:/container <image>` - Mount volume
- `docker run --name <name> <image>` - Run with custom name
- `docker start <container>` - Start stopped container
- `docker stop <container>` - Stop running container
- `docker restart <container>` - Restart container
- `docker rm <container>` - Remove container
- `docker rm -f <container>` - Force remove running container

## Container Inspection & Logs
- `docker logs <container>` - View container logs
- `docker logs -f <container>` - Follow logs in real-time
- `docker logs --tail 100 <container>` - Show last 100 log lines
- `docker inspect <container>` - Show detailed container info
- `docker stats` - Show resource usage of containers
- `docker top <container>` - Show running processes in container

## Executing Commands
- `docker exec <container> <command>` - Execute command in running container
- `docker exec -it <container> bash` - Open interactive bash shell
- `docker exec -it <container> sh` - Open shell (for alpine images)
- `docker attach <container>` - Attach to running container

## Networks
- `docker network ls` - List networks
- `docker network create <name>` - Create network
- `docker network inspect <network>` - Show network details
- `docker network connect <network> <container>` - Connect container to network
- `docker network rm <network>` - Remove network

## Volumes
- `docker volume ls` - List volumes
- `docker volume create <name>` - Create volume
- `docker volume inspect <volume>` - Show volume details
- `docker volume rm <volume>` - Remove volume
- `docker volume prune` - Remove unused volumes

## Docker Compose
- `docker-compose up` - Start services defined in docker-compose.yml
- `docker-compose up -d` - Start services in detached mode
- `docker-compose down` - Stop and remove services
- `docker-compose ps` - List services
- `docker-compose logs` - View logs from services
- `docker-compose logs -f <service>` - Follow logs for specific service
- `docker-compose build` - Build or rebuild services
- `docker-compose restart <service>` - Restart service
- `docker-compose exec <service> <command>` - Execute command in service

## Registry Operations
- `docker login` - Login to Docker Hub
- `docker push <image>` - Push image to registry
- `docker search <term>` - Search Docker Hub for images

## System Maintenance
- `docker system df` - Show Docker disk usage
- `docker system prune` - Remove unused data
- `docker system prune -a` - Remove all unused images
- `docker container prune` - Remove stopped containers
- `docker image prune` - Remove dangling images
- `docker volume prune` - Remove unused volumes

## Copy Files
- `docker cp <container>:/path /host/path` - Copy from container to host
- `docker cp /host/path <container>:/path` - Copy from host to container

## Common Use Cases
- `docker run -d -p 80:80 --name web nginx` - Run nginx web server
- `docker run -it --rm ubuntu bash` - Run temporary Ubuntu container
- `docker build -t myapp:v1 . && docker run -d -p 8080:8080 myapp:v1` - Build and run
- `docker logs -f --tail 100 $(docker ps -q)` - Follow logs of last container
- `docker exec -it $(docker ps -q -l) bash` - Shell into most recent container

## Troubleshooting
- `docker info` - Display system-wide information
- `docker version` - Show Docker version
- `docker events` - Get real-time events from server
- `docker port <container>` - Show port mappings

---

**Last Updated:** February 25, 2026
