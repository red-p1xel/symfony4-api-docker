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

Run container instances from Docker CLI:

Execute MySQL ``db`` container:

```bash
$ docker exec -it -u db bash
```

Execute ``php`` container:

```bash
$ docker exec -it -u dev php bash
```

# Combo-commands

Combo-commands for working with container instances using by `docker-compose`

1. Stop & rebuild the containers with execute command line interface for main `php` container:
    ```bash
    $ docker-compose stop ; docker-compose build ; docker-compose up -d ; docker exec -it -u dev php bash
    ```

2. Stop and remove containers:
    ```bash
    $ docker-compose stop ; docker-compose rm
    ```

3. Stop. Remove. Build & Execute main container command line interface:
    ```bash
    $ docker-compose stop ; docker-compose rm ; docker-compose stop ; docker-compose build ; docker-compose up -d ; docker exec -it -u dev php bash
    ```
4. Run command in container command line interface without keeping session
    ```bash
    $ docker exec -it -u root php bash -c "cd /var/www/app/ ; ./bin/console about"
    ```

## Create a nested project into existing container

When it’s done, we will get the sub-project in to root path of base project.
Run this commands into console of ``php`` container.

1. Go to level up directory ``/var/www/``:
    ```bash
    $ cd /var/www/
    ```

2. Create nested project into base application directory (e.g: ``/var/www/app``):
    ```bash
    $ composer create-project symfony/skeleton nested_project
    ```

3. Go to nested project directory:
    ```bash
    $ cd /var/www/app/nested_project
    ```

4. Check your current **active directory** into container instance:
    ```bash
    $ pwd
    ```

    Console output:
    ```bash
    $ /var/www/app/
    ```

5. Test working of nesting project:
    ```bash
    $ ./bin/console about
    ```

Enjoy,
and happy codding!