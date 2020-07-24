# Cheatsheet for Docker
Docker compose

```
docker-compose build
docker-compose up
```

Dockerfile

```
# creator
MANTAINER Matheus Vanzan
LABEL mylabel

# files
COPY
ADD

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

# workdir
WORKDIR /home/docky

# port
EXPOSE 3000

# last 
ENTRYPOINT
```

Usage Build

```
# spec file
docker build -f filename

# spec tag
docker build -t

# complete custom
docker build --rm -f Dockerfile -t username/docker-image:latest .
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

# run detached
docker run -d docker-image

# run it
docker run -it docker-image

# run random port
docker run -P docker-image

# run with port
docker run -p 8080:8080 docker-image

# run with env var
docker run -e MYENV=my_value"

# run with working dir (cd)
docker run -w /home/docky/

# run with volume
docker run -v $(pwd)/media:/home/docky/media

# run in network
docker run --network local-network
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

Usage networks

```
docker network create --driver bridge local-network
docker run --network local-network
```
