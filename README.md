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

# run with port
docker run -p 8080:8080 docker-image

# run with env var
docker run -e MYENV=my_value"

# run with volume
docker run -v $(pwd)/media:/home/docky/media
```

Bulk remove

```
# all containers
docker rm -vf $(docker ps -a -q)

# not active containers
docker container prune

# all images
docker rmi -f $(docker images -a -q)
```
