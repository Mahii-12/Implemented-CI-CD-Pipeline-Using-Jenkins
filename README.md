# E-Commerce Platform System
> Created a robust E-Commerce app for seamless browsing, searching, and purchasing using Java. Backed by efficient caching, it ensures swift and reliable transactions. Built on SOLID principles, it’s flexible, scalable,
delivering an efficient and satisfying shopping experience.

> Successfully implemented CRUD operations for scalable management, tested using Postman for reliable functionality.

# CI/CD
> I've defined variables application, mvnHome, dockerImage, and dockerImageTag to manage information about the application, Maven, and Docker images.

> Next, I've set up the Clone Repo stage to fetch the code from the specified GitHub repository and branch, ensuring the availability of the Maven tool for subsequent stages.

> Then, in the Build Project stage, I've utilized Maven to compile and package the project using the mvn clean install command.

> Moving on to the Build Docker Image with new code stage, I've instructed Docker to construct an image incorporating the latest code changes, assigning it the designated tag.

> Following that, I've implemented the Push Image to Remote Repo stage to upload the newly created Docker image to the remote repository, particularly DockerHub, indicating the image's tag.

> Subsequently, in the Remove running container with old code stage, I've handled the removal of any existing containers running the outdated version of the application, allowing for a clean deployment environment.

> Proceeding to the Deploy Docker Image with new changes stage, I've initiated a new container utilizing the recently updated Docker image, specifying the container's name and port mapping.

> Lastly, in the Remove old images stage, I've managed the deletion of obsolete Docker images from the repository to maintain a streamlined image registry, specifically targeting the image tagged as the latest version.

# Containerization
> After building your Spring Boot application and creating the Docker image using this modified Dockerfile, you can run the container with:

    docker build -t e-commerce-app
    docker run -p 8080:8080 e-commerce-app

    Steps:

> Containerize Microservices: 
* Packaged each microservice and its dependencies into Docker containers using Dockerfiles.
> Build Container Images:
* Created container images for each microservice using Docker build commands.
> Container Orchestration: 
* Deployed the containerized microservices to a Kubernetes cluster as MiniKube for orchestration.
> Service Discovery: 
* Used Kubernetes service objects to enable service discovery and load balancing between microservices.
> Scalability: 
* Scaled individual microservices up or down based on demand using Kubernetes scaling features.
> Continuous Deployment:
* Implemented a CI/CD pipeline to automate the building, testing, and deployment of containerized microservices.
