# Docker

## Docker Commands

* `docker build -t react-app .`: This command is used to build a Docker image. `-t` indicates the tag name, and `.` at the end indicates that the Dockerfile is in the current directory.
* `docker run ubuntu`: This command is used to run the Ubuntu image.
* `docker pull ubuntu`: This command is used to pull images from Docker Hub.
* `docker run -it ubuntu`: This command is used to run the image in interactive mode.
* `docker ps`: This command is used to see all the running processes.
* `docker ps -a`: This command is used to see all processes, including stopped ones.
* `docker start -i 274`: This command is used to start a container or image with the help of the image or container ID.
* `docker exec -it -u john 274 bash`: This command is used to execute the running Ubuntu image in interactive mode with the user "john."
* `docker images`: This command is used to display all the images available on the local machine.
* `docker image ls`: This command is also used to display all the images available on the local machine.
* `docker history react-app`: This command displays all the instructions are executed seperatly with thier size and gets stored as a seperate layer.
* `docker image prune`: This command is used remove all the dangaling images.
* `docker container prune`: This command is used remove all the stopped containers.
* `docker image rm react-app`: This command is used remove one or multiple images
* `docker build -t reactapp:1 .`: This command is used to build the docker image with a tag name.
* `docker image remove react-app:1`: This command is used untag an image.
* `docker image tag react-app:latest react-app:1`: This command is used to set a tag for already existing image.
* `docker image tag react-app:2 react-app:latest`: This command is also used to update the lastest tag to the newly built docker image.