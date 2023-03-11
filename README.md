### Dockerfiles

Dockerfile is a declarative way of creating our own images. Docker will give us some syntax to create our own images.

Dockerfile reference: https://docs.docker.com/engine/reference/builder/

File name should be Dockerfile.

### How to build image from Dockerfile
...
docker build -t [docker-hub-URL]/[your-username]/[Image-name]:version .
...

Example: docker build -t docker.io/rmahesh9/from:v1 .

### How to push image to Dockerhub
...
docker push [docker-hub-URL]/[your-username]/[Image-name]:version
...
