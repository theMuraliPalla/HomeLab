# Dockerfile Complete Guide

Comprehensive guide to Dockerfile instructions with examples and best practices.

---

## Key Dockerfile Instructions

### FROM - Base Image
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

### WORKDIR - Set Working Directory
```dockerfile
WORKDIR /app
WORKDIR /usr/src/myapp
```
**Purpose:** Sets the working directory for subsequent instructions  
**Effect:** Creates directory if it doesn't exist  
**Note:** All relative paths will be relative to this directory

---

### COPY - Copy Files
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

### ADD - Copy Files (Advanced)
```dockerfile
ADD archive.tar.gz /app/
ADD https://example.com/file.txt /app/
```
**Purpose:** Like COPY but can extract archives and download URLs  
**Best Practice:** Prefer COPY unless you need ADD's special features

---

### RUN - Execute Commands
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

### CMD - Default Command
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

### ENTRYPOINT - Container Executable
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

### EXPOSE - Document Ports
```dockerfile
EXPOSE 80
EXPOSE 8000 8080
EXPOSE 3000/tcp
EXPOSE 53/udp
```
**Purpose:** Document which ports the container listens on  
**Note:** Doesn't actually publish ports (use `-p` flag with `docker run`)

---

### ENV - Environment Variables
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

### ARG - Build Arguments
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

### VOLUME - Mount Points
```dockerfile
VOLUME /data
VOLUME ["/var/log", "/var/db"]
```
**Purpose:** Create mount point for persistent data  
**Effect:** Data in volumes persists beyond container lifecycle

---

### USER - Set User Context
```dockerfile
RUN adduser --disabled-password --gecos '' appuser
USER appuser
```
**Purpose:** Set user for subsequent instructions  
**Best Practice:** Don't run as root in production

---

### HEALTHCHECK - Container Health
```dockerfile
HEALTHCHECK --interval=30s --timeout=3s \
  CMD curl -f http://localhost:8000/health || exit 1

HEALTHCHECK CMD python healthcheck.py
```
**Purpose:** Tell Docker how to test if container is healthy  
**Options:** `--interval`, `--timeout`, `--start-period`, `--retries`

---

### ONBUILD - Trigger Instructions
```dockerfile
ONBUILD COPY . /app
ONBUILD RUN pip install -r requirements.txt
```
**Purpose:** Instructions to execute when image is used as base  
**Use Case:** Creating base images for specific frameworks

---

## Complete Dockerfile Examples

### Python Flask Application
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

### Node.js Application
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

### Multi-Stage Build (Go Application)
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

## Dockerfile Best Practices

### 1. Layer Caching - Order Matters
```dockerfile
# Good: Dependencies first (cached if unchanged)
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .

# Bad: Code changes invalidate dependency cache
COPY . .
RUN pip install -r requirements.txt
```

### 2. Minimize Layers
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

### 3. .dockerignore File
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

### 4. Security Best Practices
```dockerfile
# Run as non-root user
RUN adduser --disabled-password appuser
USER appuser

# Use specific versions
FROM python:3.11.5-slim

# Don't store secrets in image
# Use build args or runtime env vars
```

### 5. Image Size Optimization
```dockerfile
# Use alpine base images
FROM python:3.11-alpine

# Clean package manager cache
RUN pip install --no-cache-dir package

# Multi-stage builds
# Keep only runtime dependencies in final stage
```

---

**Last Updated:** February 25, 2026
