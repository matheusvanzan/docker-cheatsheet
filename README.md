# Cheatsheet for Docker

Dockerfile

```
# user
ENV USER docky
RUN useradd -ms /bin/bash $USER
RUN usermod --password $USER $USER

# python virtualenv
ENV VIRTUAL_ENV=/home/$USER/env
RUN python -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# no password for sudo
RUN echo "ALL ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/nopass
```

Usage Build

```
# build
docker build --rm -t docker-image:latest .
```

Usage Checks

```
# check port
docker port image-hash
```

Usage Run

```
# run with name
docker run --name meu-container

# run detatched
docker run -d docker-image

# run random port
docker run -P docker-image

# run
docker run -p 8080:8080 -v $(pwd)/media:/home/docky/media docker-image
```

Remove all

```
# containers
docker rm -vf $(docker ps -a -q)

# containers inativos
docker container prune

# images
docker rmi -f $(docker images -a -q)
```
