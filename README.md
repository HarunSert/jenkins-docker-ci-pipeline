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
3. The Docker image is tagged with the Jenkins build number.
4. The same image is also tagged as `latest`.
5. Jenkins authenticates to Docker Hub using Jenkins Credentials.
6. Both Docker image tags are pushed to Docker Hub.

## Project Structure

```text
.
├── Dockerfile
├── Jenkinsfile
├── index.html
└── README.md
```

## Dockerfile

The application runs on the lightweight Nginx Alpine image.

```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html
```

The `index.html` file is copied into the default Nginx web directory and served by the container.

## Jenkins Pipeline

The Jenkins pipeline is defined as code in the `Jenkinsfile`.

The pipeline contains the following stages:

### 1. Checkout

Jenkins retrieves the source code from the GitHub repository.

### 2. Build Docker Image

Jenkins builds the Docker image and tags it using the Jenkins build number.

Example:

```text
harunsert/nginx-jenkins-demo:21
```

The same image is also tagged as:

```text
harunsert/nginx-jenkins-demo:latest
```

### 3. Push to Docker Hub

Jenkins authenticates to Docker Hub using credentials stored securely in Jenkins Credentials.

The following images are then pushed:

```text
harunsert/nginx-jenkins-demo:<BUILD_NUMBER>
harunsert/nginx-jenkins-demo:latest
```

## Docker Image

Docker Hub image:

```text
harunsert/nginx-jenkins-demo
```

## Jenkins Credentials

Docker Hub credentials are not stored directly in the repository.

Jenkins Credentials are used to securely provide:

- Docker Hub username
- Docker Hub password/token

The pipeline accesses these credentials during the Docker Hub login process.

## CI Workflow

```text
Developer
    |
    v
GitHub Repository
    |
    v
Jenkins Pipeline
    |
    v
Docker Build
    |
    +----------------------+
    |                      |
    v                      v
Build Number Tag        Latest Tag
    |                      |
    +----------+-----------+
               |
               v
           Docker Hub
```

## Skills Demonstrated

This project demonstrates practical experience with:

- Jenkins Pipeline as Code
- CI pipeline configuration
- Docker image creation
- Docker image tagging
- Docker Hub integration
- Jenkins Credentials
- Git and GitHub integration
- Build versioning
- Containerized Nginx applications
- Automated artifact publishing

## Future Improvements

Possible improvements for this project include:

- Adding automated container tests
- Adding image vulnerability scanning
- Deploying the image to Kubernetes
- Adding Helm-based deployment
- Adding deployment stages to the Jenkins pipeline
- Adding rollback support
- Adding notifications for pipeline failures
- Integrating monitoring and observability

## Author

**Harun Sert**

DevOps Engineer

LinkedIn:  
https://www.linkedin.com/in/harun-sert-819236233/
