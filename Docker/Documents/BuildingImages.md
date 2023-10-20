# Docker Images

* Image: Docker images consist of various elements such as a trimmed-down OS, configuration settings, and third-party libraries. An image contains everything needed for an application to run.

* Container: A container is similar to a virtual machine, providing an isolated environment for running an application. Containers have their own file system and derive their files from an image.

* `FROM`:
    - The `FROM` instruction is used to inherit packages or images from Docker Hub. For .NET applications, the Microsoft Container Registry (MCR) is used to import packages. Examples:
      ```
      FROM baseImage
      FROM baseImage:tag
      ```

* `WORKDIR`:
    - The `WORKDIR` instruction sets the current working directory, which all subsequent commands in the Dockerfile will consider as the base directory. Examples:
      ```
      WORKDIR /path/to/workdir
      WORKDIR relative/path
      ```

* `ADD`:
    - The `ADD` instruction is used to add multiple files or directories from the host to the image. It can also perform additional tasks like extracting ZIP files and adding files from URLs.

* `COPY`:
    - The `COPY` instruction is similar to `ADD` but does not have additional functionality like extracting ZIP files or adding files from URLs. Examples:
      ```
      COPY hello.txt /absolute/path
      COPY hello.txt relative/to/workdir
      ```

* `RUN`:
    - The `RUN` instruction is used to run commands in the Dockerfile. It can execute both Linux and Windows commands.

* `ENV`:
    - The `ENV` instruction sets environment variables. These variables are used to configure the application, such as setting API_URL or other important values.

* `EXPOSE`:
    - The `EXPOSE` instruction specifies the port on which the application will listen. For example, many React applications listen on port 3000, while Angular applications may use port 4200.

* `USER`:
    - The `USER` instruction is used to specify the user running the application within the container. It's advisable to create a user with the `RUN` command and then make that user run the application. By default, the root user runs the application, which can pose security risks.

* `CMD`:
    - The `CMD` instruction is used to specify the command that runs when the container is executed. It is typically used to start the application (e.g., `npm start`, `ng serve`, `dotnet run`). The `CMD` command is only executed when the image is run, not during image building.

* `ENTRYPOINT`:
    - The `ENTRYPOINT` instruction is similar to `CMD` but provides more rigidity in defining the command that runs when the container is executed. To override the `CMD` command at runtime, you need to use the `--entrypoint` option and specify the new command.

* `.dockerignore`:
    - You can create a `.dockerignore` file to specify files and directories that should be ignored when building the Docker image, similar to a `.gitignore` file.


* In the docker image it stores every modified data as a seperate layer and each and every command in the docker file gets executes and stored in a seperate layer, so if the already built image is built again then it gets all the data from cache memory and fasts the building process, so while creating the docker file if you feel any instruction gets modified then its better to write at them after writing all the stable instructions(The instructions which wont get modified easily) and changing instructions need to be written at the end (In a application if the code gets changed then the copy instruction need to re-executed and stored in the same layer)