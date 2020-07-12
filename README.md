# Learn-docker

### Terminology
##### Images  
The blueprints of our application which form the basis of containers. In the demo above, we used the docker pull command to download the busybox image.
##### Containers
Created from Docker images and run the actual application. We create a container using docker run which we did using the busybox image that we downloaded. A list of running containers can be seen using the docker ps command.
##### Docker Daemon  
The background service running on the host that manages building, running and distributing Docker containers. The daemon is the process that runs in the operating system which clients talk to.
##### Docker Client  
The command line tool that allows the user to interact with the daemon. More generally, there can be other forms of clients too - such as Kitematic which provide a GUI to the users.
##### Docker Hub 
A registry of Docker images. You can think of the registry as a directory of all available Docker images. If required, one can host their own Docker registries and can use them for pulling images.

----
### Commands
- check if installation is fine \
`docker run hello-world` \
When you call run, the Docker client finds the image (hello-world in this case), loads up the container and then runs a command in that container. \
##### Base images 
They are images that have no parent image, usually images with an OS like ubuntu, busybox or debian.
##### Child images 
They are images that build on base images and add additional functionality.
##### Official images  
images that are officially maintained and supported by the folks at Docker. These are typically one word long. In the list of images above, the python, ubuntu, busybox and hello-world images are official images.
##### User images
images created and shared by users like you and me. They build on base images and add additional functionality. Typically, these are formatted as user/image-name.

- Search docker images \
`docker search image-name`
- #### docker run \
Running the run command with the -it flags attaches us to an interactive tty in the container. ( tty stands for TeleTYpewriter ) \
Now we can run as many commands in the container as we want. \
`docker run -it busybox sh`

- pull a new image on the local system \
`docker pull busybox`

- check locally installed images \
`docker images`

- check currently running containers \
`docker ps`

- check previously run containers \
`docker ps -a`

- Cleaning unused docker containers \
`docker rm [container-id-1 container-id-2 ...]`

- delete all containers at once \
`docker rm $(docker ps -a -q -f status=exited)` \
This command deletes all containers that have a status of exited. In case you're wondering, the -q flag, \
only returns the numeric IDs and -f filters output based on conditions provided. \
One last thing that'll be useful is the --rm flag that can be passed to docker run which automatically deletes \
the container once it's exited from. For one off docker runs, --rm flag is very useful. 

- Prune can also be used to achieve the above behavior
`docker conatiner prune`

- Remove unwanted images
`docker rmi [images]`


#### Static sites
- `docker run -d -P --name static-site prakhar1989/static-site` \
In the above command, -d will detach our terminal, -P will publish all exposed ports to \
random ports and finally --name corresponds to a name we want to give. \
Now we can see the ports by running the docker port [CONTAINER] command

- `docker port static-site` - check the exposed ports of continer
- `docker stop static-site` - to stop the container either with container id or container name

# Useful Links
- https://docker-curriculum.com
- 
