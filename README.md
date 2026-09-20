# Jenkins Docker CI Pipeline

A simple CI pipeline demonstrating automated Docker image build and publishing using Jenkins.

## Architecture

GitHub → Jenkins → Docker Build → Docker Hub

## Technologies

- Jenkins
- Docker
- Docker Hub
- Nginx
- Git
- GitHub

## Pipeline Flow

1. Jenkins checks out the source code from GitHub.
2. A Docker image is built using the project's Dockerfile.
3. Jenkins authenticates to Docker Hub using Jenkins Credentials.
4. The Docker image is pushed to Docker Hub.

## Project Structure

```text
.
├── Dockerfile
├── Jenkinsfile
├── index.html
└── README.md
