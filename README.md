# Docker Symfony (php7.4 - nginx - mysql8 - elk - node)
Docker-symfony gives you everything you need for developing Symfony application.
This complete stack run with docker and [docker-compose](https://docs.docker.com/compose/).

## Installation

1. Create a `.env` from the `.env.dist` file. Adapt it according to your symfony application

    ```bash
    cp .env.dist .env
    ```
2. Build/run containers

    ```bash
    $ ./start-dev.sh
    ```
3. Prepare Symfony app
   1. Composer install & create database

       ```bash
       $ docker-compose exec php74-service bash
       $ composer install
       # Symfony
       $ sf doctrine:database:create
       $ sf doctrine:schema:update --force
       # Only if you have `doctrine/doctrine-fixtures-bundle` installed
       $ sf doctrine:fixtures:load --no-interaction
       ```
4. Create db phpStorm
   ```bash
      Name: localhoast
      General -> Tab
      Host: localhost Port:{LOCAL_MYSQL_PORT}
      User: {MYSQL_USER}
      Password:{MYSQL_PASSWORD}
      Database: MYSQL_DATABASE
   ```
   
