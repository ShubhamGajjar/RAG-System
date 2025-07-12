# Docker Setup Guide for RAG System

This guide will help you set up and run the RAG System using Docker.

## Prerequisites

1. **Install Docker Desktop** (if not already installed):

   - **macOS**: Download from [Docker Desktop for Mac](https://docs.docker.com/desktop/install/mac-install/)
   - **Windows**: Download from [Docker Desktop for Windows](https://docs.docker.com/desktop/install/windows-install/)
   - **Linux**: Follow the [Docker Engine installation guide](https://docs.docker.com/engine/install/)

2. **Verify Docker installation**:
   ```bash
   docker --version
   docker-compose --version
   ```

## Project Structure

```
RAG-System/
├── backend/
│   ├── Dockerfile
│   ├── .dockerignore
│   ├── main.py
│   └── requirements.txt
├── frontend/
│   ├── Dockerfile
│   ├── .dockerignore
│   ├── package.json
│   └── src/
├── docker-compose.yml
└── DOCKER_SETUP.md
```

## Quick Start

1. **Clone and navigate to the project**:

   ```bash
   cd /path/to/RAG-System
   ```

2. **Build and start all services**:

   ```bash
   docker-compose up --build
   ```

3. **Access the applications**:
   - **Frontend**: http://localhost:3000
   - **Backend API**: http://localhost:8000
   - **Backend API Docs**: http://localhost:8000/docs

## Development Commands

### Start services in detached mode

```bash
docker-compose up -d
```

### View logs

```bash
# All services
docker-compose logs

# Specific service
docker-compose logs backend
docker-compose logs frontend

# Follow logs in real-time
docker-compose logs -f
```

### Stop services

```bash
docker-compose down
```

### Rebuild and restart

```bash
docker-compose down
docker-compose up --build
```

### Access container shell

```bash
# Backend container
docker-compose exec backend bash

# Frontend container
docker-compose exec frontend sh
```

## Individual Service Commands

### Backend only

```bash
# Build and run backend
docker-compose up backend

# Build backend image
docker build -t rag-backend ./backend

# Run backend container
docker run -p 8000:8000 rag-backend
```

### Frontend only

```bash
# Build and run frontend
docker-compose up frontend

# Build frontend image
docker build -t rag-frontend ./frontend

# Run frontend container
docker run -p 3000:3000 rag-frontend
```

## Troubleshooting

### Common Issues

1. **Port already in use**:

   ```bash
   # Check what's using the port
   lsof -i :8000
   lsof -i :3000

   # Kill the process or change ports in docker-compose.yml
   ```

2. **Permission issues**:

   ```bash
   # On Linux/macOS, you might need to run with sudo
   sudo docker-compose up
   ```

3. **Build cache issues**:

   ```bash
   # Clear Docker build cache
   docker system prune -a

   # Rebuild without cache
   docker-compose build --no-cache
   ```

4. **Container not starting**:

   ```bash
   # Check container status
   docker-compose ps

   # Check container logs
   docker-compose logs [service-name]
   ```

### Reset Everything

```bash
# Stop and remove all containers, networks, and volumes
docker-compose down -v

# Remove all images
docker system prune -a

# Rebuild from scratch
docker-compose up --build
```

## Production Deployment

For production deployment, consider:

1. **Using production Dockerfiles** with multi-stage builds
2. **Setting up proper environment variables**
3. **Configuring reverse proxy (nginx)**
4. **Setting up SSL certificates**
5. **Using Docker volumes for persistent data**

## Environment Variables

You can create a `.env` file in the root directory to customize the setup:

```env
# Backend
BACKEND_PORT=8000
PYTHONUNBUFFERED=1

# Frontend
FRONTEND_PORT=3000
REACT_APP_API_URL=http://localhost:8000
```

Then reference them in `docker-compose.yml`:

```yaml
environment:
  - PORT=${BACKEND_PORT}
```

## Next Steps

1. **Customize the configuration** based on your needs
2. **Add database services** (PostgreSQL, Redis, etc.) to docker-compose.yml
3. **Set up CI/CD pipelines** for automated deployment
4. **Configure monitoring and logging**

## Support

If you encounter any issues:

1. Check the troubleshooting section above
2. Review the Docker and docker-compose logs
3. Ensure all prerequisites are properly installed
4. Verify your system meets the minimum requirements
