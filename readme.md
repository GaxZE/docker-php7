# Docker-PHP7

A quick and easy way to setup your PHP application using Docker and docker-compose. This will setup a developement environment with PHP7-fpm, MariaDB and Nginx.

Getting started
---------------

Download [Docker](https://www.docker.com/products/overview). If you are on Mac or Windows, [Docker Compose](https://docs.docker.com/compose) will be automatically installed. On Linux, make sure you have the latest version of [Compose](https://docs.docker.com/compose/install/).


## Usage
~~~
git clone git@github.com:GaxZE/docker-php7.git
cd docker-php7
cp .env.default .env
docker-compose up -d
~~~

### Structure

~~~
├── app
│   └── public
│   	└── index.php
├── database
├── docker-compose.yml
├── fpm
│   ├── Dockerfile
│   └── supervisord.conf
├── nginx
│   ├── Dockerfile
│   └── default.conf
~~~

- `app` is the directory for project files. The Nginx config is pointing to `/var/app/`, which can be changed in `nginx/default.conf`
- `database` is where MariDB will store the database files.
- Visit http://localhost:5000/ after build.

## Helpful commands

~~~
docker ps # to list all containers.
docker exec -it <CONTAINER_ID> bash # ssh into container.
docker images # list all images created.
~~~
