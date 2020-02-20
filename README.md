# Symfony Container

This image is configured for use developing and deploying Symfony applications. It is specific to the needs of Dayspring Partners, but can be used as a starting point.

This is based on the official php docker image. See the documentation for the [official image](https://hub.docker.com/_/php).

## How to use this image

### Create a Dockerfile in your own project

```
FROM mdensondayspring/symfony:latest
COPY . /usr/src/myapp
WORKDIR /usr/src/myapp
CMD [ "php", "./your-script.php" ]
```

Then, run the commands to build and run the Docker image:

```
$ docker build -t my-php-app .
$ docker run -it --rm --name my-running-app my-php-app
```

### Example docker-compose.yml

```
symfony:
  image: 'mdensondayspring/symfony:latest'
  container_name: '${REPOSITORY_NAME}_symfony'
  hostname: '${REPOSITORY_NAME}-symfony'
  environment:
    DATABASE_URL: '${DEV_DATABASE_URL}'
  volumes:
    - symfony-app:/usr/src/symfony

volumes:
  symfony-app: {}
```