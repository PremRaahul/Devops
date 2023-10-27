# Docker

## Docker Commands

* `docker version`: This command is used to check the current version of the docker that is installed
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
* `docker login`: This command is used for signing into docker hub account using command prompt
* `docker push iampremraahul/react-app:3`: This command is used to push the image into the docker hub 
* `docker image save -o react-app.zip iampremraahul/react-app:3`: This command is convert the docker image into a zip file (if you have any doughts regarding this command then you can use `docker image save --help`)
* `docker image load -i react-app.zip`: This command is used to load the image which is saved locally
* `docker run -d react-app`: This command is used to run the docker command in ditached mode so that we access the terminal without terminating or stoping the image
* `docker run -d --name blue-sky react-app`: This command used to give the container name manully and run it in a ditached mode 
* `docker logs 3356`: This command is used to see the logs of the container that is running and we can explore about this with the help of `docker logs --help`
* `docker run -d -p 3000:3000 --name c1 react-app`: This command is used for port publishing from host to the container
* `docker exec -it c1 sh` - `docker exec c1 sh`: The execute command is used execute the commands in a running container
* `docker stop c1`: This command is used to stop a running container
* `docker start c1`: This command is used to start a stopped container
* `docker rm c1` - `docker container rm c1`: This command is used to remove a container
* `docker container rm -f c1`: If the container is runnig and you try to remove that container then remove the container force fully or we need to stop the container and remove it
* `docker volume create app-data`: This command is used create a volume in docker and this volume can act as centralised file system among the multiple containers
* `docker run -d -p 5000:3000 -v app-data:/app/data/ react-app`: This command is used for volume mapping with the container that is running
* `docker cp 8400fa6dba6d:/app/log.txt .`: This command is used to copy a file from the container to the current directory of the host
* `docker cp secret.txt 8400fa6dba6d:/app/`: This command is used to copy the file from the host to the container
* `docker run -d -p 3000:3000 -v $(pwd):/app/ react-app`: This command is used to map the project directory in the host with project directory of the container, any changes that are made in the host project can also be seen in the container that is currently running