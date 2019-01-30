symfony4-api-docker
===================

Complete stack for building API's and running Symfony 4 Skeleton (latest) into Docker containers using docker-compose.

# Containers

``db`` - MySQL 5.7

``php`` - PHP 7.2.10 with Xdebug

``apache`` - Apache2 Server (httpd)

# Installation

Clone this repository:

```bash
$ git clone https://github.com/red-p1xel/symfony4-api-docker
```

Put your exist Symfony application to project root path or create a new project using ``composer`` into Docker container:

Build & configure containers:

```bash
$ docker-compose build
```

At this moment, Docker will execute all configurations that we set up. When it’s done, you can launch your containers!

```bash
$ docker-compose up -d
```

# How execute containers?

Run container instances from command line in your Terminal:

Execute MySQL ``db`` container:

```bash
$ docker exec -it -u db bash
```

Execute ``php`` container:

```bash
$ docker exec -it -u dev php bash
```

## Installation of Symfony4 with composer

Run this commands into command line interface of ``php`` container:

```bash
$ cd app/ 
```
```bash
$ composer create-project symfony/skeleton tmp
```

When it’s done, we will get the project to the root path.

```bash
$ cp -Rf /var/www/app/tmp/. .
$ rm -Rf /var/www/app/tmp
```

Enjoy,

and happy codding!