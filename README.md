# Docker

### Commands (Ubuntu 14.04)

```sh
$ uanme -r   // check to see if kernel version is > 3.10
$ sudo apt-get install curl   // install curl
$ curl -fsSL https://get.docker.com/ | sh   // install docker
$ docker -v   // verify docker installed
$ docker run hello-world   // should display "Hello from Docker"
```
![](https://denibertovic.com/talks/supercharge-development-env-using-docker/img/docker-flow.png)

Image Source: https://denibertovic.com/talks/supercharge-development-env-using-docker

### Docker CLI Example

```sh
$ docker login
$ docker pull denibertovic/postgres
$ docker run -d -t denibertovic/postgres
$ docker run -i -t debian /bin/bash
$ docker run -d -t postgres
$ docker run -d -t postgres:9.3
$ docker ps
$ docker logs 2344d8a4e916
$ docker stop 2344d8a4e916
$ docker kill 2344d8a4e916
$ docker start 2344d8a4e916
```
![](docker_ps.PNG)

### Docker Build Image

Dockerfile:
```sh
FROM      debian:wheezy
ENV DEBIAN_FRONTEND noninteractive

...

RUN apt-get -qq update
RUN apt-get -qq -y install postgresql-9.3 \
    postgresql-client-9.3 postgresql-contrib-9.3
ADD postgresql.conf /etc/postgresql/9.3/main/postgresql.conf
...

CMD /usr/local/bin/start_postgres.sh
```
$ docker build -t postgres .
