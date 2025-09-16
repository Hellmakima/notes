# Docker

## Analogy

**Dockerfile**: like a Technical Manual
`docker build -t <image_name> .` makes an **image**: Factory Mold
`docker run <image_name>` makes a **container**: Assembled Machine

---

## Important Commands

- `docker images` lists all images
- `docker build -t <image_name> .` builds an image
- `docker rmi <image_name>` deletes an image
- `docker ps -a` lists all containers
- `docker run <image_name>` runs a container
- `docker stop <container_id>` stops a container
- `docker rm <container_id>` deletes a container

---

## Docker Desktop

- you need to keep this running to use the cli commands
- easily manage your images and containers
- tap into your image's resource usage

---

## Dockerfile

A `Dockerfile` is a text file containing a set of instructions that the Docker engine executes to build a Docker image.
Usually sits in the root directory of your project.

```dockerfile
# FROM: Specifies the base image to use for the Docker image.
# This defines the starting point for your image, here using Python 3.11 on a slim variant.
FROM python:3.11-slim

LABEL maintainer="Your Name <your@email.com>"

# WORKDIR: Sets the working directory inside the container where commands will be executed.
# This ensures that all subsequent instructions (COPY, RUN, etc.) are run relative to this directory.
WORKDIR /app

# COPY: Copies files or directories from the host machine into the container.
# This copies all the files from the current directory (.) to the /app directory inside the container.
COPY . /app

# RUN: Executes commands in the container to install dependencies or perform setup tasks.
# In this case, it's installing the Python dependencies listed in requirements.txt.
RUN pip install --no-cache-dir -r requirements.txt

# CMD: Specifies the command to run when the container starts.
# Here, it runs a Python script (app.py) when the container is started.
CMD ["python", "app.py"]

# EXPOSE: Exposes a port from the container to the host machine.
# This allows the container to listen on port 8080.
EXPOSE 8080
# you'll need to run `docker run -p 8080:8080 <image_name>` to access the app

# ENV: Sets environment variables for the container.
# Here we define the APP_ENV variable to specify the environment as 'production'.
ENV APP_ENV=production
# use .env for sensitive data like secrets, api keys, etc. Do not use ENV for this
```

**Layer Caching in Docker** (each command in a Dockerfile creates a layer)
Docker optimizes image builds by caching each layer, so the order in the Dockerfile matters: instructions that are less likely to change (like installing dependencies) should come before more changeable parts (like copying source code) to avoid unnecessary rebuilds of unchanged layers.

---

## Images

A Docker image is a lightweight, standalone, and executable software package that serves as a read-only template for creating Docker containers. It contains:

- Application code
- Runtime environment (e.g., Python, Node.js)
- System tools and libraries
- Settings and configurations (e.g., Environmental variables, network configurations)

Once done with your Dockerfile, you can build the image with `docker build .` (Dockerfile is in curr dir)

- name your build: `docker build -t my_app .`
- help: `docker build --help`

**Sharing and releasing images**

- push to docker hub: `docker push <image_name>`
- pull from docker hub: `docker pull <image_name>`
  You can also use github packages to share your images.
  Docker Hub is a registry for sharing Docker images.

---

## Containers

Containers are the runtime instances of Docker images. They are isolated from each other and from the host machine.

- every `docker run` makes a new container
- start interactively `docker run -i my_app`
- start and delete after run `docker run --rm my_app`

## Other Docker Features

### Volumes

Volumes are a way to persist data between container runs. They are created using the `docker volume create` command.

### Docker Networks

Docker networks allow containers to communicate with each other. They are created using the `docker network create` command.

### Multi-stage builds

Multi-stage builds allow you to build an image from multiple stages. This can be useful for building images that require multiple steps to build, such as building a database image, frontend, backend image and then combining them into a final image.

### Docker Swarm (for orchestration)

- Docker Swarm is Docker's native clustering and orchestration tool, allowing you to deploy and manage multi-container applications across a cluster of machines.

- It's a simpler alternative to Kubernetes for managing containers at scale, although Kubernetes is more feature-rich.

### And Many More

Logging, Healthchecks, Build contexts, Secrets, and more.

## Docker Compose

Used to handle multiple docker containers using `docker-compose.yml` file

~~Next up **Kubernetes**. hopefully soon :)~~

Kubernetes is an open-source container orchestration platform that automates deploying, scaling, and managing containerized applications. It was built by Google in 2014 based on an internal tool called Borg. Considering the complexity and benefits of kubernetes, I'll skip it for now.
