# DevOps Commands Reference Guide

Complete reference for Git, Linux, Docker, Python, and Dockerfile commands for DevOps engineers.

---

## Table of Contents
1. [Git Commands](#git-commands)
2. [Linux Commands](#linux-commands)
3. [Docker Commands](#docker-commands)
4. [Python & PIP Commands](#python--pip-commands)
5. [Dockerfile Instructions](#dockerfile-instructions)

---

## Git Commands

### Setup & Configuration
- `git config --global user.name "Your Name"` - Set your username
- `git config --global user.email "email@example.com"` - Set your email

### Repository Initialization
- `git init` - Initialize a new Git repository in current directory
- `git clone <url>` - Clone a remote repository to your local machine

### Basic Workflow
- `git status` - Show current branch and modified files
- `git add <file>` - Stage specific file for commit
- `git add .` - Stage all changed files
- `git commit -m "message"` - Commit staged changes with a message
- `git push` - Push commits to remote repository
- `git pull` - Fetch and merge changes from remote repository

### Branching
- `git branch` - List all local branches
- `git branch <name>` - Create new branch
- `git checkout <branch>` - Switch to specified branch
- `git checkout -b <branch>` - Create and switch to new branch
- `git merge <branch>` - Merge specified branch into current branch
- `git branch -d <branch>` - Delete a branch

### Viewing History
- `git log` - Show commit history
- `git log --oneline` - Show condensed commit history
- `git diff` - Show unstaged changes
- `git diff --staged` - Show staged changes

### Undoing Changes
- `git reset <file>` - Unstage a file
- `git reset --hard` - Discard all local changes
- `git revert <commit>` - Create new commit that undoes specified commit
- `git checkout -- <file>` - Discard changes in working directory

### Remote Operations
- `git remote -v` - List remote repositories
- `git remote add origin <url>` - Add a remote repository
- `git fetch` - Download changes without merging
- `git push -u origin <branch>` - Push branch and set upstream

---

## Linux Commands

### File & Directory Management
- `ls` / `ls -la` - List files (with details and hidden files)
- `cd <directory>` - Change directory
- `pwd` - Print working directory
- `mkdir <name>` - Create directory
- `rm <file>` - Remove file
- `rm -rf <directory>` - Remove directory recursively
- `cp <source> <dest>` - Copy files
- `mv <source> <dest>` - Move or rename files
- `touch <file>` - Create empty file
- `find <path> -name <pattern>` - Search for files

### File Viewing & Editing
- `cat <file>` - Display file contents
- `less <file>` - View file with pagination
- `head <file>` - Show first 10 lines
- `tail <file>` - Show last 10 lines
- `tail -f <file>` - Follow file updates in real-time (logs)
- `grep <pattern> <file>` - Search text in files
- `nano <file>` / `vi <file>` - Text editors

### Permissions & Ownership
- `chmod 755 <file>` - Change file permissions
- `chown user:group <file>` - Change file owner
- `sudo <command>` - Execute command as superuser

### Process Management
- `ps aux` - List all running processes
- `top` / `htop` - Monitor system resources
- `kill <pid>` - Terminate process by ID
- `kill -9 <pid>` - Force kill process
- `jobs` - List background jobs
- `bg` / `fg` - Background/foreground jobs

### Network & Connectivity
- `ping <host>` - Test network connectivity
- `curl <url>` - Transfer data from URLs
- `wget <url>` - Download files
- `ssh user@host` - Secure shell connection
- `scp <source> user@host:<dest>` - Secure copy files
- `netstat -tuln` - Show listening ports
- `ifconfig` / `ip addr` - Display network interfaces

### System Information
- `df -h` - Show disk space usage
- `du -sh <directory>` - Show directory size
- `free -h` - Show memory usage
- `uname -a` - System information
- `uptime` - System uptime and load

### Package Management
- `apt update` / `apt upgrade` - Update packages (Ubuntu/Debian)
- `apt install <package>` - Install package
- `yum install <package>` - Install package (CentOS/RHEL)

### Archive & Compression
- `tar -czvf archive.tar.gz <directory>` - Create compressed archive
- `tar -xzvf archive.tar.gz` - Extract archive
- `zip -r archive.zip <directory>` - Create zip file
- `unzip archive.zip` - Extract zip file

### Text Processing
- `awk '{print $1}' <file>` - Process columns
- `sed 's/old/new/g' <file>` - Stream editor for replacing text
- `sort <file>` - Sort lines
- `uniq` - Remove duplicate lines
- `wc -l <file>` - Count lines

### DevOps Specific
- `docker ps` - List running containers
- `docker logs <container>` - View container logs
- `systemctl status <service>` - Check service status
- `systemctl restart <service>` - Restart service
- `journalctl -u <service>` - View service logs
- `crontab -e` - Edit scheduled tasks
- `env` - Show environment variables
- `export VAR=value` - Set environment variable

### Piping & Redirection
- `command1 | command2` - Pipe output to another command
- `command > file` - Redirect output to file (overwrite)
- `command >> file` - Append output to file
- `command 2>&1` - Redirect stderr to stdout

---

## Docker Commands

### Images
- `docker images` - List all local images
- `docker pull <image>` - Download image from registry
- `docker build -t <name>:<tag> .` - Build image from Dockerfile
- `docker rmi <image>` - Remove image
- `docker tag <image> <new-name>:<tag>` - Tag an image
- `docker history <image>` - Show image layers

### Containers
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

### Container Inspection & Logs
- `docker logs <container>` - View container logs
- `docker logs -f <container>` - Follow logs in real-time
- `docker logs --tail 100 <container>` - Show last 100 log lines
- `docker inspect <container>` - Show detailed container info
- `docker stats` - Show resource usage of containers
- `docker top <container>` - Show running processes in container

### Executing Commands
- `docker exec <container> <command>` - Execute command in running container
- `docker exec -it <container> bash` - Open interactive bash shell
- `docker exec -it <container> sh` - Open shell (for alpine images)
- `docker attach <container>` - Attach to running container

### Networks
- `docker network ls` - List networks
- `docker network create <name>` - Create network
- `docker network inspect <network>` - Show network details
- `docker network connect <network> <container>` - Connect container to network
- `docker network rm <network>` - Remove network

### Volumes
- `docker volume ls` - List volumes
- `docker volume create <name>` - Create volume
- `docker volume inspect <volume>` - Show volume details
- `docker volume rm <volume>` - Remove volume
- `docker volume prune` - Remove unused volumes

### Docker Compose
- `docker-compose up` - Start services defined in docker-compose.yml
- `docker-compose up -d` - Start services in detached mode
- `docker-compose down` - Stop and remove services
- `docker-compose ps` - List services
- `docker-compose logs` - View logs from services
- `docker-compose logs -f <service>` - Follow logs for specific service
- `docker-compose build` - Build or rebuild services
- `docker-compose restart <service>` - Restart service
- `docker-compose exec <service> <command>` - Execute command in service

### Registry Operations
- `docker login` - Login to Docker Hub
- `docker push <image>` - Push image to registry
- `docker search <term>` - Search Docker Hub for images

### System Maintenance
- `docker system df` - Show Docker disk usage
- `docker system prune` - Remove unused data
- `docker system prune -a` - Remove all unused images
- `docker container prune` - Remove stopped containers
- `docker image prune` - Remove dangling images
- `docker volume prune` - Remove unused volumes

### Copy Files
- `docker cp <container>:/path /host/path` - Copy from container to host
- `docker cp /host/path <container>:/path` - Copy from host to container

### Common Use Cases
- `docker run -d -p 80:80 --name web nginx` - Run nginx web server
- `docker run -it --rm ubuntu bash` - Run temporary Ubuntu container
- `docker build -t myapp:v1 . && docker run -d -p 8080:8080 myapp:v1` - Build and run
- `docker logs -f --tail 100 $(docker ps -q)` - Follow logs of last container
- `docker exec -it $(docker ps -q -l) bash` - Shell into most recent container

### Troubleshooting
- `docker info` - Display system-wide information
- `docker version` - Show Docker version
- `docker events` - Get real-time events from server
- `docker port <container>` - Show port mappings

---

## Python & PIP Commands

### Python Execution
- `python --version` - Show Python version
- `python script.py` - Run Python script
- `python -m module` - Run module as script
- `python -c "print('hello')"` - Execute Python code directly
- `python -i script.py` - Run script in interactive mode
- `python -u script.py` - Run with unbuffered output (useful for logs)

### Python Interactive
- `python` - Start Python REPL/interactive shell
- `exit()` or `Ctrl+D` - Exit interactive shell
- `help(function)` - Get help on function/module
- `dir(object)` - List object attributes

### PIP - Package Management
- `pip --version` - Show pip version
- `pip install <package>` - Install package
- `pip install <package>==1.0.0` - Install specific version
- `pip install -r requirements.txt` - Install from requirements file
- `pip uninstall <package>` - Uninstall package
- `pip list` - List installed packages
- `pip show <package>` - Show package details
- `pip freeze` - Output installed packages in requirements format
- `pip freeze > requirements.txt` - Export dependencies to file
- `pip install --upgrade <package>` - Upgrade package
- `pip install --upgrade pip` - Upgrade pip itself
- `pip search <term>` - Search PyPI (deprecated, use web)

### Virtual Environments (venv)
- `python -m venv myenv` - Create virtual environment
- `myenv\Scripts\activate` - Activate venv (Windows)
- `source myenv/bin/activate` - Activate venv (Linux/Mac)
- `deactivate` - Deactivate virtual environment
- `which python` - Show which Python is being used (Linux/Mac)
- `where python` - Show which Python is being used (Windows)

### Virtual Environments (virtualenv)
- `pip install virtualenv` - Install virtualenv
- `virtualenv myenv` - Create virtual environment
- `virtualenv -p python3.9 myenv` - Create with specific Python version

### Package Building & Distribution
- `pip install -e .` - Install package in editable/development mode
- `python setup.py sdist` - Create source distribution
- `python setup.py bdist_wheel` - Create wheel distribution
- `pip wheel .` - Build wheel for current project
- `twine upload dist/*` - Upload package to PyPI

### Dependency Management
- `pip check` - Verify installed packages have compatible dependencies
- `pip list --outdated` - Show outdated packages
- `pip install --upgrade-strategy eager <package>` - Upgrade with dependencies
- `pipdeptree` - Show dependency tree (install first)

### Python Path & Modules
- `python -m site` - Show site-packages location
- `python -c "import sys; print(sys.path)"` - Show Python search path
- `python -c "import module; print(module.__file__)"` - Find module location

### Testing & Code Quality
- `python -m pytest` - Run tests with pytest
- `python -m unittest discover` - Run unit tests
- `python -m pylint script.py` - Lint Python code
- `python -m black script.py` - Format code with Black
- `python -m flake8 script.py` - Check style guide
- `python -m mypy script.py` - Type checking

### Performance & Debugging
- `python -m timeit "code"` - Measure execution time
- `python -m cProfile script.py` - Profile script performance
- `python -m pdb script.py` - Debug script with pdb
- `python -m trace --trace script.py` - Trace execution

### HTTP Server
- `python -m http.server` - Start HTTP server on port 8000
- `python -m http.server 8080` - Start on specific port

### JSON Processing
- `python -m json.tool file.json` - Pretty-print JSON
- `echo '{"key":"value"}' | python -m json.tool` - Format JSON from pipe

### Environment & System
- `python -c "import os; print(os.environ)"` - Show environment variables
- `python -c "import platform; print(platform.system())"` - Show OS info
- `python -c "import sys; print(sys.executable)"` - Show Python executable path

### Common DevOps Patterns
- `pip install --no-cache-dir <package>` - Install without cache (Docker)
- `pip install --user <package>` - Install for current user only
- `pip download <package>` - Download package without installing
- `pip install --proxy http://proxy:port <package>` - Install via proxy
- `pip config list` - Show pip configuration
- `pip config set global.index-url <url>` - Set custom PyPI mirror

### Requirements File Management
- `pip freeze | grep <package>` - Find specific package version
- `pip install -r requirements.txt --upgrade` - Upgrade all packages
- `pip-compile requirements.in` - Generate locked requirements (pip-tools)

### Alternative Package Managers
- `poetry install` - Install dependencies (Poetry)
- `poetry add <package>` - Add package (Poetry)
- `pipenv install` - Install from Pipfile (Pipenv)
- `pipenv install <package>` - Add package (Pipenv)
- `conda install <package>` - Install with Conda

### Useful One-Liners
- `python -m venv venv && source venv/bin/activate && pip install -r requirements.txt` - Setup project
- `pip list --format=freeze > requirements.txt` - Export clean requirements
- `pip install --quiet --upgrade pip setuptools wheel` - Update build tools

---

## Dockerfile Instructions

### Key Dockerfile Instructions

#### FROM - Base Image
```dockerfile
FROM python:3.11-slim
FROM node:18-alpine
FROM ubuntu:22.04
FROM nginx:latest
```
**Purpose:** Specifies the base image to build upon  
**Best Practice:** Use specific versions, avoid `latest` in production  
**Alpine:** Minimal Linux distribution (smaller image size)

---

#### WORKDIR - Set Working Directory
```dockerfile
WORKDIR /app
WORKDIR /usr/src/myapp
```
**Purpose:** Sets the working directory for subsequent instructions  
**Effect:** Creates directory if it doesn't exist  
**Note:** All relative paths will be relative to this directory

---

#### COPY - Copy Files
```dockerfile
COPY requirements.txt .
COPY . /app
COPY src/ /app/src/
COPY --chown=user:group file.txt /destination/
```
**Purpose:** Copy files from host to container  
**Syntax:** `COPY <source> <destination>`  
**Best Practice:** Copy dependencies file first for better layer caching

---

#### ADD - Copy Files (Advanced)
```dockerfile
ADD archive.tar.gz /app/
ADD https://example.com/file.txt /app/
```
**Purpose:** Like COPY but can extract archives and download URLs  
**Best Practice:** Prefer COPY unless you need ADD's special features

---

#### RUN - Execute Commands
```dockerfile
RUN apt-get update && apt-get install -y curl
RUN pip install --no-cache-dir -r requirements.txt
RUN npm install
```
**Purpose:** Execute commands during image build  
**Best Practice:** Chain commands with `&&` to reduce layers  
**Note:** Each RUN creates a new layer

**Multi-line RUN:**
```dockerfile
RUN apt-get update && \
    apt-get install -y \
    curl \
    wget \
    git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
```

---

#### CMD - Default Command
```dockerfile
CMD ["python", "app.py"]
CMD ["nginx", "-g", "daemon off;"]
CMD python app.py
```
**Purpose:** Default command to run when container starts  
**Format:**
- Exec form (preferred): `CMD ["executable", "param1", "param2"]`
- Shell form: `CMD command param1 param2`

**Note:** Only last CMD is used; can be overridden at runtime

---

#### ENTRYPOINT - Container Executable
```dockerfile
ENTRYPOINT ["python", "app.py"]
ENTRYPOINT ["docker-entrypoint.sh"]
```
**Purpose:** Configure container to run as executable  
**Difference from CMD:** ENTRYPOINT is not easily overridden

**Combined with CMD:**
```dockerfile
ENTRYPOINT ["python"]
CMD ["app.py"]
# Results in: python app.py
# Can override CMD: docker run image test.py -> python test.py
```

---

#### EXPOSE - Document Ports
```dockerfile
EXPOSE 80
EXPOSE 8000 8080
EXPOSE 3000/tcp
EXPOSE 53/udp
```
**Purpose:** Document which ports the container listens on  
**Note:** Doesn't actually publish ports (use `-p` flag with `docker run`)

---

#### ENV - Environment Variables
```dockerfile
ENV APP_ENV=production
ENV PORT=8000
ENV PATH="/app/bin:${PATH}"
ENV DB_HOST=localhost \
    DB_PORT=5432 \
    DB_NAME=mydb
```
**Purpose:** Set environment variables  
**Scope:** Available during build and runtime  
**Override:** Can be overridden with `docker run -e`

---

#### ARG - Build Arguments
```dockerfile
ARG VERSION=1.0
ARG PYTHON_VERSION=3.11

FROM python:${PYTHON_VERSION}-slim

RUN echo "Building version ${VERSION}"
```
**Purpose:** Variables only available during build  
**Usage:** `docker build --build-arg VERSION=2.0 .`  
**Difference from ENV:** ARG values don't persist in final image

---

#### VOLUME - Mount Points
```dockerfile
VOLUME /data
VOLUME ["/var/log", "/var/db"]
```
**Purpose:** Create mount point for persistent data  
**Effect:** Data in volumes persists beyond container lifecycle

---

#### USER - Set User Context
```dockerfile
RUN adduser --disabled-password --gecos '' appuser
USER appuser
```
**Purpose:** Set user for subsequent instructions  
**Best Practice:** Don't run as root in production

---

#### HEALTHCHECK - Container Health
```dockerfile
HEALTHCHECK --interval=30s --timeout=3s \
  CMD curl -f http://localhost:8000/health || exit 1

HEALTHCHECK CMD python healthcheck.py
```
**Purpose:** Tell Docker how to test if container is healthy  
**Options:** `--interval`, `--timeout`, `--start-period`, `--retries`

---

#### ONBUILD - Trigger Instructions
```dockerfile
ONBUILD COPY . /app
ONBUILD RUN pip install -r requirements.txt
```
**Purpose:** Instructions to execute when image is used as base  
**Use Case:** Creating base images for specific frameworks

---

### Complete Dockerfile Examples

#### Python Flask Application
```dockerfile
# Use Python base image
FROM python:3.11-slim

# Set working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    gcc \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements and install Python packages
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# Create non-root user
RUN useradd -m -u 1000 appuser && chown -R appuser:appuser /app
USER appuser

# Expose port
EXPOSE 5000

# Health check
HEALTHCHECK --interval=30s --timeout=3s \
  CMD python -c "import requests; requests.get('http://localhost:5000/health')"

# Set environment variables
ENV FLASK_APP=app.py
ENV FLASK_ENV=production

# Run application
CMD ["python", "app.py"]
```

---

#### Node.js Application
```dockerfile
# Multi-stage build
FROM node:18-alpine AS builder

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm ci --only=production

# Copy source code
COPY . .

# Build application
RUN npm run build

# Production stage
FROM node:18-alpine

WORKDIR /app

# Copy only necessary files from builder
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package*.json ./

# Expose port
EXPOSE 3000

# Run as non-root user
USER node

# Start application
CMD ["node", "dist/index.js"]
```

---

#### Multi-Stage Build (Go Application)
```dockerfile
# Build stage
FROM golang:1.21-alpine AS builder

WORKDIR /build

COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o app

# Production stage
FROM alpine:latest

RUN apk --no-cache add ca-certificates

WORKDIR /root/

# Copy only the binary
COPY --from=builder /build/app .

EXPOSE 8080

CMD ["./app"]
```

---

### Dockerfile Best Practices

#### 1. Layer Caching - Order Matters
```dockerfile
# Good: Dependencies first (cached if unchanged)
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .

# Bad: Code changes invalidate dependency cache
COPY . .
RUN pip install -r requirements.txt
```

#### 2. Minimize Layers
```dockerfile
# Good: Single layer
RUN apt-get update && \
    apt-get install -y package1 package2 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Bad: Multiple layers
RUN apt-get update
RUN apt-get install -y package1
RUN apt-get install -y package2
```

#### 3. .dockerignore File
```
# .dockerignore
.git
.gitignore
node_modules
venv
__pycache__
*.pyc
.env
Dockerfile
.dockerignore
README.md
tests/
```

#### 4. Security
```dockerfile
# Run as non-root user
RUN adduser --disabled-password appuser
USER appuser

# Use specific versions
FROM python:3.11.5-slim

# Don't store secrets in image
# Use build args or runtime env vars
```

#### 5. Small Images
```dockerfile
# Use alpine base images
FROM python:3.11-alpine

# Clean package manager cache
RUN pip install --no-cache-dir package

# Multi-stage builds
# Keep only runtime dependencies in final stage
```

---

## Bonus: Python Date/Time Function

```python
from datetime import datetime

def get_formatted_datetime():
    """
    Returns current date and time in dd-mm-yyyy HH:MM:SS format
    """
    now = datetime.now()
    return now.strftime("%d-%m-%Y %H:%M:%S")

# Date only (dd-mm-yyyy)
def get_formatted_date():
    return datetime.now().strftime("%d-%m-%Y")

# Example usage
print(get_formatted_datetime())  # Output: 25-02-2026 14:30:45
```

**Common format codes:**
- `%d` - Day (01-31)
- `%m` - Month (01-12)
- `%Y` - Year (4 digits)
- `%H` - Hour 24-hour (00-23)
- `%I` - Hour 12-hour (01-12)
- `%M` - Minute (00-59)
- `%S` - Second (00-59)
- `%p` - AM/PM
- `%f` - Microsecond

---

**Document Version:** 1.0  
**Last Updated:** February 25, 2026  
**Author:** DevOps Reference Guide
