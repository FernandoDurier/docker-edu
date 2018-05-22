# Docker Magic
This section explain more about the docker process and workflow.
In order to install docker please follow these steps below:

## MAC setup
1. brew cask install docker
2. Activate Docker via its ui whenever it finished its download
3. brew install docker-compose

## Windows Setup
1. Try to exchange your machine for a MAC or at least one that runs Linux distribution ... And do not try VMs for this (I know you thought about it ...)
2. If you use windows 10, just go to Docker website and download it
* If not windows 10 user, really consider step 1, else, try the chocolatey (windows apt-get), and make the installation through it
3. Follow this reference -> [Study of Docker on Windows Machines](./docs/docker-on-windows-machines.pdf) 

## Dockerfile
The dockerfile is the script that will build each docker image you need.

1. At root level of a project create a extensionless file Dockerfile
2. Write your needed commands there to build your adequate image, e.g. [Dockerfile](./docs/Dockerfile)
3. Probably there will be things you won't want to upload when creating your container, one of them are the project dependencies, so create a file .dockerignore like .gitignore, e.g. [dockerignore](./docs/.dockerignore)
4. In order to build the container using the Dockerfile, issue this command on your terminal:
    `docker build <container name> <path to the Folder containing the Dockerfile>`
5. Now that it is built, lets run the container:
    `docker run -d -p <container Port>:<host Port> <container name>`
6. Now, if everything went well on the aforementioned steps, you should be able to test the service dockerized through the localhost and the ports you mapped. E.g., normally we choose common ports like 3000 or 8080 for mapping.

* Example:
1. `docker build -t war/ui .`
2. `docker build -t war/backend .`
3. `docker run -d -p 3000:3000 war/backend`
4. `docker run -d -p 8080:8080 war/ui`
* **Now it is possible to check these services on `localhost:3000` and `localhost:8080`**

## Docker-Compose
Now that we have everything setup and ready, we can compose and manage the container creation process through files and a reduced set of commands ...

1. Createa a new folder
2. Get inside it 
3. Pick each of the dockerized projects github(svm) references 
4. On terminal, type: `git submodule init`
5. On terminal, type: `git submodule add <github reference either ssh or https>`
6. On terminal, whenever any of those repositories added before receive an update, please type: `git submodule update`
7. Now that the environment is setup, lets make the one file that will make every magic of docker-compose a reality, create a new file called docker-compose and its extension will yml(yet another markup language)
8. Edit the yml as we edited in here -> [docker-compose](./docker-compose.yml)
9. As you saw there, we declared the services we dockerized, the path where the dockerfile can be found (`build`), the image that will be generated through their Dockerfiles process (`image`) and finally the port mapping (`ports`), i.e. in which port of the container the service will be exposed and in which port of the host the docker's port will be exposed.
10. Now that everything is mapped and defined, go to the folder where the yml file is in and issue the following commands: `docker-compose up`
11. In order to stop and clear the containers created, issue the following command: `docker-compose down`

## In order to use this project for the first time:
1. Install Docker and Docker Compose
2. Go to the folder and issue the command `git submodule init`
3. Issue the command `git submodule update`
4. Issue the command `docker-compose Build`
5. Issue the command `docker-compose Up`
6. Issue the command `docker-compose Down`
7. Do all needed modification on the submodules and commit and push inside their folders, and everything will be alright
 

