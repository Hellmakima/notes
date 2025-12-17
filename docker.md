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
# you can use `.dockerignore` to ignore files

# RUN: Executes commands in the container to install dependencies or perform setup tasks.
# In this case, it's installing the Python dependencies listed in requirements.txt.
RUN pip install --no-cache-dir -r requirements.txt
# This command runs only when the container is built.

# CMD: Specifies the command to run when the container starts.
# Here, it runs a Python script (app.py) when the container is started.
CMD ["python", "app.py"]
# This command runs the when the container starts.

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

- `docker compose up` creates containers (if missing) as specified in this file. Starts them, reuses existing volumes
- `docker compose down` Stops AND deletes the containers. Does NOT delete data unless you add `-v`, networks are removed, images stay

**example of compose.yml file**

```yaml
version: "3.9" # Compose file format version

services:
  frontend:
    image: node:18 # Base image with Node.js v18
    working_dir: /app # Set working directory inside the container
    volumes:
      - ./frontend:/app # Mount local frontend code into container
    ports:
      - "3000:3000" # Expose frontend dev server on port 3000
    command: ["npm", "start"] # Start React dev server
    environment:
      - NODE_ENV=development # Environment variable for React
    depends_on:
      - backend # Wait for backend to be ready

  backend:
    build: ./backend # Build backend image from Dockerfile in ./backend
    working_dir: /app # Set working directory inside the container
    volumes:
      - ./backend:/app # Mount local backend code into container
    ports:
      - "5000:5000" # Expose backend API on port 5000
    command: ["python", "app.py"] # Run backend app
    environment:
      - APP_ENV=production # Environment variable for backend
      - MONGO_URI=mongodb://mongo:27017/mydb # MongoDB connection string
    depends_on:
      - mongo # Wait for MongoDB before starting

  mongo:
    image: mongo:6 # Official MongoDB image version 6
    ports:
      - "27017:27017" # Expose MongoDB on default port
    volumes:
      - mongo_data:/data/db # Persist MongoDB data

volumes:
  mongo_data: # Named volume for MongoDB persistence
```

~~Next up **Kubernetes**. hopefully soon :)~~

Kubernetes is an open-source container orchestration platform that automates deploying, scaling, and managing containerized applications. It was built by Google in 2014 based on an internal tool called Borg. Considering the complexity and benefits of kubernetes, I'll skip it for now.

