# MEAN Stack CRUD Application - DevOps Assignment

This project contains a full-stack MEAN (MongoDB, Express, Angular, Node.js) application, containerized and ready for deployment with a CI/CD pipeline.

## Project Structure

- `backend/`: Express.js & Node.js API.
- `frontend/`: Angular 15 application.
- `nginx/`: Nginx reverse proxy configuration.
- `docker-compose.yml`: Orchestrates MongoDB, Backend, and Frontend.
- `.github/workflows/deploy.yml`: GitHub Actions pipeline.

## Prerequisites

- [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) installed locally.
- A Cloud VM (Ubuntu) with Docker installed.
- A Docker Hub account.

## Local Setup & Containerization

1.  **Clone the repository**:
    ```bash
    git clone <your-repo-url>
    cd <repo-name>
    ```

2.  **Run with Docker Compose**:
    ```bash
    docker-compose up --build
    ```
    - Frontend: `http://localhost` (Port 80 via Nginx)
    - Backend API: `http://localhost:8080/api`
    - MongoDB: `mongodb://localhost:27017`

## CI/CD Pipeline Configuration

The project uses GitHub Actions for CI/CD. To enable it:

1.  **Set up Repository Secrets** in GitHub:
    - `DOCKER_USERNAME`: Your Docker Hub username.
    - `DOCKER_PASSWORD`: Your Docker Hub password or access token.
    - `VM_IP`: The public IP of your Ubuntu VM.
    - `SSH_PRIVATE_KEY`: The private SSH key used to access your VM.

2.  **Push to `main` branch**:
    - Every push to the `main` branch will trigger the pipeline.
    - It builds images, pushes them to Docker Hub, and automatically updates the app on your VM.

## Deployment Details

- **Nginx**: Acts as a reverse proxy. It serves the Angular frontend and routes all `/api` requests to the Node.js backend.
- **Database**: MongoDB runs as a Docker container with persistent volume storage.
- **Network**: All containers communicate within a dedicated bridge network.

## Task Deliverables Status

- [x] Dockerfiles for Frontend & Backend
- [x] Docker Hub image push capability
- [x] Docker Compose deployment
- [x] MongoDB Docker integration
- [x] GitHub Actions CI/CD Pipeline
- [x] Nginx Reverse Proxy (Port 80)
- [x] Documentation & README
