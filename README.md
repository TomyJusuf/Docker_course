# Docker_course

### Docker images & Docker container

    * Images                                    * Container
    - RUNTIME ENVIRONMENT                       - ISOLATED PROCESS
    - APPLICATION CODE         →RUN→            - RUNNING INSTANCE OF AN IMAGES
    - ANY DEPENDENCIES                          - RUN OUR APPLICATION
    - EXTRA CONFIGURATION
    - COMMANDS

---

## IMAGES

#### How create dockerfile ?

Create dockerfile in my project

1.  Inside a project I must create file with name Dockerfile
2.  Inside file Dockerfile

            FROM node:16-alpine                //Base Image: It starts with a Node.js 17 environment using a lightweight Alpine Linux image.
            WORKDIR /app                       //Working Directory: It sets the working directory in the container to /app.
            COPY . .                           //It copies your application code [(app.js), the Dockerfile, and the package.json and package-lock.json files] into [the /app directory in the container].
            RUN npm install                    //Install Dependencies: It runs npm install to install all the dependencies specified in package.json.
            EXPOSE 4000                        //Expose Port: It indicates(oznacuje) that your application will use port 4000
            CMD [ "node","app.js" ]            //Run Application: It specifies the command to start your application (node app.js) when the container starts.

#### Build app

    := tag as version;
    docker build -t <name_image_app_i_choice> .        // the dot there is important
    docker build -t <name_image_app_i_choice>:v1 .

#### How Ignore file

Same as .gitignore the Docker have same ignore constructor file

.dockerignore

    node_modules             //ignore node_modules
    *.md                     //ignore all file with root .md

#### INFO ABOUT IMAGES

    docker images                 // Give me ID, TAGS, SIZE, INFO about the Images
    Sumare:
    By using .dockerignore, you can optimize the Docker build process
    and ensure that only necessary files are included in the Docker image.

---

#### RUN & STOP

##### RUN CONTAINER PROCESS

    p=post; -d=detached; a=all; -i=interactive terminal;

    docker run --name <container_n> -p [post_n:port_n] -d <images_n>        //It will run container with name_my_container on port ...
    docker start <contaainer_n>                 //  Dont need speficied again
    docker start -i <my_container>              //  Attach terminal for interactive input
    docker ps -a                                //  List of all containers,including stoped ones
    docker ps                                   //  List of containers which are currently running
    docker ps -q                                //  List only container IDs
    docker ps --filter
    docker ps --format

##### STOP & ALL RUNNING PROCESSING OR DELETING

    docker stop <name_of_container>             // Stop
    docker stop $(docker ps -q)                 // Stop
    docker rm   $(docker ps -a -q)              // Remove
    docker system prune -a                      // Clean up
    docker system prune -a volumes              // Clean up everything else

##### MANAGING IMAGES & CONTAINERS

    --rm=remove after close/end; myapp:<...> = version|tag;
    docker build -t myapp:v1                    //Create images
    docker start -i myapp_c                     //Attach terminal for interactive input
    docker run --name nodemon_app -p 4000:4000 --rm myapp:<version or how we can named tag>
