# Docker-Compose

The docker compose file is used to run the multiple containers at the same time

# Commands

* `docker-compose up`: This command is used to run the docker compose file

* The docker compose file starts with the version and this version should match with the docker engine version and the services in the compose file indicates main building blocks of your application like frontend,backend and database, These names in the compose file can be written as your wish. 
* The build property is used to build the image based on the docker file path and ports is used to for port mapping. 
* The environment property is used to declare the environment variable like database connection string. 
* The image property is used to pull the image from the docker hub.
* The volumes property is used to map the volume with directory and create a new volumes

``` yaml
version: '3.8'

services:
  web:
    build: ./frontend
    ports:
      - 3000:3000
  api:
    build: ./backend
    ports:
      - 3001:3001
    environment:
      DB_URL: mongodb://db/vidly
    volumes:
      - ./backend:/app
  db:
    image: mongo:4.0-xenial
    ports:
      - 27017:27017
    volumes:
      - vidly:/data/db

volumes:
  vidly:
    

```

* `docker-compose build`: This command is used to build the docker compose file and start the multiple containers.
* `docker-compose build --no-cache`: This command is used to build the docker compose file with no cache.
* `docker-compose up -d`: This command is used to run the docker compse file in the detached mode.
* `docker-compose ps`: This command is used see all the processes or containers running under this compose file.
* `docker-compose down`: This command is used to remove or stop the all running containers
* `docker-compose logs`: This command is used to logs of the docker-compose containers
* `./backend:/app`: We can also volume map host project directory with the container project directory
* To perform the database migration we need to run the migration file while building docker-compose file so that first we need to intialise the database image and then run the migrations, we can use wait for it until the image gets loaded then we can run the  migration file 
* To run tests we can create seperate container and use the already created container in that and run the tests