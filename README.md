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
COPY config/nopass /etc/sudoers.d/
```

Usage

```
# build
docker build --rm -t django-nginx:latest .

# run
docker run -p 8080:8080 -v $(pwd)/media:/home/vanzan/media django-nginx
```

Remove all

```
# containers
docker rm -vf $(docker ps -a -q)

# images
docker rmi -f $(docker images -a -q)
```
