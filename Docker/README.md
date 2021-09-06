# Docker

### 1. What is Docker?
Docker is a containerization platform that enables you to build, test and deploy software solutions; reliably and quickly. Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. It packages your application and all its dependencies together in the form of a container, to ensure that your application works seamlessly in any machine or environment be it like Development/Test/production without facing runtime environment conflicts.

### 2. What is container and why is it used for?
Container is like a software bucket comprising everything (code & dependencies) necessary to run the software independently. Containers are a form of operating system virtualization with few differences.
1) Containers are completely isolated environments as in they can have their own services, processes, networking interfaces and mounts just like a VM except that they all share same OS kernel.
2) Containers are lightweight. Inside a container are all the necessary executables, binary code, libraries, and configuration files, making them easy to ship and run with same expected results on different machines.

### 3. How are containers different from virtual machines (VMs)?
![image](https://user-images.githubusercontent.com/43535914/129036731-2feb45ff-1d3a-451d-967c-9e911869dc9d.png)

Virtual machine | Container
--------------- | ---------
Virtual machines run on hypervisor which provides virtual hardware resources to each of the VM.	| Containers run on docker engine.
Each VM has a full OS with its own kernel, memory management and virtual device drivers. (complete isolation) |	Containers share the host OS kernel, with each container having its own set of binaries and libraries. (less isolation)
Vm's are of hardware virtualization (An abstraction of the physical hardware turning one server into many servers)	| Containers are for OS-level virtualization (An abstraction at the application layer that packages code and dependencies together.)
VM’s ship with bunch of packages that may not be needed for application | Containers only ship with what exactly needed for application.
VM’s takes minutes to boot up as it should load entire OS.	| Containers boot up faster just in few seconds
Each VM has its own independent file system. |	Layered file system
Support for monolithic architecture |	Support for micro services architecture.
Running VM’s can be backed up.	| No need for backups. Application data lives in a volume which is shared between containers.
VMs take more space as they include everything (in GBs) | 	Containers take very less space (Images are typically in tens of MBs). 
VM’s have complete isolation from each other. Since VM’s don’t rely on the underlying OS, you can have different types of OS like windows or linux based on the same hypervisor | Docker has less isolation as more resources are shared are shared between the container like the kernel.

### 4. In which scenarios would you use containers and in which you would prefer to use VMs?
You should choose VMs when:
- you need run an application which requires all the resources and functionalities of an OS
- you need full isolation and security

You should choose containers when:
- you need a lightweight solution
- Running multiple versions or instances of a single application

### 5. Why Docker?
- It provides a lightweight and faster alternative to virtual machines.
- It is a convenient way to package applications and integrates very well with the continuous delivery model. No need for long installation manual to be shift along with the software.
- Docker is useful to automate the deployment of applications inside a software containers, which makes the applications easy to ship and run virtually anywhere (i.e, platform independent). The Docker container processes run on the host kernel, unlike VM which runs processes in guest kernel.
- Building the software followed by shipping can be easily automated. All the dependencies, libraries are taken and bundled in the image. The images are in ready to run state which can be straight away deployed at the customer end.
- In case of docker containers all the environments are just the same and the image runs efficiently in any environment ie., what works in Dev will work in Prod environment.

### 6. Docker Architecture:
![image](https://user-images.githubusercontent.com/43535914/129138794-0f63c6c3-6c64-405e-9355-2862d2d9337b.png)

`Docker host:` 
Docker host is the machine physical or virtual on which docker is installed.

It is a client-server architecture with following components.

**`1) Docker engine`** gets installed on the Docker host. It is the underlying implementation of containerization technology that supports the end to end work flows required for building, shipping and running container based applications.

**`2) Docker daemon(dockerd)`** is a continuous running program on the docker host. It is the core of the docker engine. Daemon creates and manages the docker objects such as images, containers, networks, volumes etc.

**`3) REST API`** communicate with the daemon process and provide instructions.

**`4) Docker client`** is a command line interface.

Note:

dockerd command is used to run daemon while docker commands are the client commands that are used by an user to interact with docker.


### 7. Explain the following Docker objects:
**1) Dockerfile &emsp;&emsp; 2) image &emsp;&emsp; 3) Container &emsp;&emsp; 4) network &emsp;&emsp; 5) volume**

**`1) DockerFile:`** DockerFile is a configuration file with build instructions for docker images

**`2) Image:`** Image is a static snapshot/read-only template which is used to create a docker container. Can be considered to be the "source code" for the containers. 

**`3) Container:`** Containers are running instances of Docker Images that are isolated, have their own environment and set of running processes. They hold the entire package needed to run an application. It includes the operating system, user added files, meta-data, etc. Container live only as long as the process inside it is alive. Once the process is complete then it exits.

**`4) Networks:`** Networking is about communication among processes, and Docker’s networking is no different. Docker networking is primarily used to establish communication between Docker containers and the outside world via the host machine where the Docker daemon is running.

**`5) Volumes:`** Mechanism for persisting data generated by and used by containers. However, volumes are independent of the containers life cycle.

Note:

When you install docker, it creates folder structure at /var/lib/docker. This is where docker stores all its data by default. It contains information about containers, volumes, images, storage driver, etc

![image](https://user-images.githubusercontent.com/43535914/129155805-c82ae744-8f6e-4d72-b164-3d0945a396ca.png)


### 8. Is it possible to run windows container on top of linux host and viceversa?
Docker containers share the underlying kernel of host OS. Docker can run any flavor of OS on top of it as long as they are all based on the same kernel. Let’s say you have a system with an Ubuntu OS with Docker installed on it. This means docker can run a container based on distribution like debian, fedora, suse or centos. But you won’t be able to run a windows container on a Docker host with Linux OS as linux kernel doesn't support windows. For that you would require docker on a windows server. But you can run linux containers on top of windows OS.

*Not being able to run another kernel on the OS? Isn’t that a disadvantage?*

The answer is No! Because unlike hypervisors, Docker is not meant to virtualize and run different Operating systems and kernels on the same hardware. The main purpose of Docker is to containerize applications and to ship them and run them.

### 9. Explain the following:
**1) Namespace &emsp;&emsp; 2) cgroups &emsp;&emsp; 3) Union file system**

One host can run multiple containers with a degree of isolation maintained between the containers using namespaces and control groups behind the scene.

**`1) Namespace:`** Docker makes use of kernel namespaces to provide the isolated workspace. Each container run in its separate namespace. Processes in a namespace can only interact with resources or processes that are part of the same namespace. In short, **it limits what a container can see.**
Docker Engine uses the following namespaces on Linux:
-  MNT namespace for managing filesystem mount points.
-  NET namespace for managing network interfaces. (that gives you the ip address and eth0 interface)
-  UTS namespace for isolating kernel and version identifiers (helps in setting up the hostname for a container)
-  PID namespace for process isolation.
-  IPC (inter process communication) namespace for managing access to IPC resources.
-  
**Ex:** &emsp; Consider an application running inside a container. If we list services on the container then the application would be running with a process id and if we list the services running on host then we will find the same application running with different PID on host. This indicate that all processes are infact running on the same host but separated into their containers using namespaces.

**`2) CGroups (Control groups:`** A cgroup limits an application to a specific set of resources. Control groups allow Docker Engine to share available hardware resources to containers and optionally enforce limits and constraints on the resource usage like Memory, CPU, block I/O, network. In short, **it limits how much a container can use** (metering & limiting). 

Below are some of the cgroups that docker engine uses:
-  Memory cgroup for managing accounting, limits and notifications.
-  CPU group for managing user/system CPU time and usage.
-  CPUSet cgroup for binding a group to specific CPU.
-  BlkIO cgroup for measuring & limiting amount of block IO by group.
-  Devices cgroup for reading/writing access devices.
-  Freezer cgroup for freezing a group. Useful for cluster batch scheduling, process migration and debugging without affecting prtrace.

**`3) Union file systems (UnionFS):`**  Layered file system

Docker operate by creating layers, making them very lightweight and fast. It allows files and directories to be transparently overlaid one over the other but appear to be one file system. Since images use union file system, each line of instruction in the Dockerfile adds a layer on the previous one to form the final docker image. Also, during image pull from registry, only the layers which have changed are downloaded.

**Ex:** &emsp; Consider an application that uses a Dockerfile which is similar to previously built application. Lets say, new Dockerfile has first 3 lines same as previous Dockerfile. When you build image for new application, since the first three layers of both the applications are the same, docker doesn’t build the first three layers. Instead it reuses the same three layers it built for the first application from the cache and only creates the last two layers. This way Docker builds images faster and efficiently saves disk space

![image](https://user-images.githubusercontent.com/43535914/129241810-0062287b-21fa-4891-861e-d03445e7bab3.png)


### 10. How do you manage docker as a non-root user?
By default docker daemon always runs as a root user. ie., if you run any docker command without sudo it results in permission denied error.
If you want to run commands without sudo, first create a docker group.

     sudo groupadd docker
The docker group grants privileges equivalent to the root user. Now add your user to the docker group 

    sudo usermod -aG docker <username> 
    
Once done logout and login back to get this group membership replicated.

### 11. Explain the following Docker terminologies:
**1) Registry &emsp;&emsp; 2) Repository**

**`1) Registry:`** Registry is a service responsible for hosting and distributing images. A registry is a collection of repositories. The default registry for Docker is **DockerHub**. You can also set your own “private and trusted” registry (Ex: Harbor) or cloud based registries like AWS Container Registry, Azure container registry, etc.

**`2) Repository:`** A Docker Repository is a collection of related images with same name which have different tags (i.e., you can store one or more versions of a specific image). These tags are an alphanumeric identifiers(like 1.0 or 1.0-alpine or latest) attached to images within a repository.

There are two types of repositories:
-  User repositories &emsp;&emsp;&emsp;	Contain images contributed by docker user
-  Top level repositories &emsp;&emsp; Controlled by docker. These are also known as official images
User repositories take form of `username/repo-name:tag` where as top level repositories only have `repository-name:tag`

**Ex:**

     To pull nginx image from specific repository - docker pull rekhad/my-app:1.0
     To pull official nginx image from Docker Hub - docker pull nginx:1.21


### 12. Explain basic workflow of Docker?
![image](https://user-images.githubusercontent.com/43535914/129311935-d42ec4b2-9689-46e2-bbb4-1ce6bfb67757.png)

We will never deploy an application directly as a container. We first deploy our application as an image then we run the image to get a container. Docker will run containers from locally available images. If the image is not available locally then the docker engine first downloads the image on to the host from the configured registry(Ex: DockerHub, Harbor, etc) and then run containers from it.

Image can be created using three ways: 
-  Using Dockerfile
-  Download image directly from docker hub.
-  Using docker commit message and convert to convert a container into an image.


### 13. Explain networking in Docker
here are three default networks created on a host upon docker installation.
- Bridge
- Host
- None
- Overlay network (in Docker swarm)

**`1) Bridge network:`**  A bridge is the default network a container gets attached to. The bridge network is a private, internal network created by docker on the host. All containers attach to this network by default and they get an internal IP address, usually in the range 170.17.x.x . Containers can access each other using this internal IP if required. To access any of these containers from outside-world, the docker bridge architecture maps ports of these containers to port on the docker host.

![image](https://user-images.githubusercontent.com/43535914/129453147-a9c7c123-de56-4ab6-a2c6-2c21599780fa.png)

**`2) Host network:`**  The host network adds a container on the host's network stack. There is no separate isolated network maintained between host machine and the container. So containers behave just like any other process running on the host. No internal ip address is assigned for containers (Containers will use the host ip address) and no need to publish ports as well.

For example, if you were to run a web server on port 5000 in a web-app container attached to the host network, it is automatically accessible on the same port externally, without requiring to publish the port using the -p option.

*Limitations of host network:*

When we have multiple containers using same port on the same docker host, there would be conflict because the requested port on the docker host is already in use.

**`3) None network:`**  The containers are not attached to any network and does not have access to the external network or other containers. It is isolated from all other networks. Use the none network if you want to completely disable the network stack on a container. 

**`4) Overlay network:`**  An overlay network is a computer network that is built on top of another network and is used for communication between containers on different hosts. It is primarily used in the context of docker swarm.


### 14. What happens when a docker container runs out of memory?
By default, if an out-of-memory (OOM) error occurs, the kernel kills processes in a container. To change this behavior, use the --oom-kill-disable option. Only disable the OOM killer on containers where you have also set the -m/--memory option. If the -m flag is not set, the host can run out of memory and the kernel may need to kill the host system’s processes to free memory.

### 15. What happens when you run a Docker container from Ubuntu image?
When you run a docker container from an Ubuntu image, it runs an instance of Ubuntu image and exits immediately. This is because containers are meant to run a specific task or process. Once the task is complete, the container exits. If you look at the docker file for ubuntu image, you will see that it uses bash as the default command. Now bash is not really a process. It is a shell that listens for inputs from a terminal, if it cannot find one it exits.

### 16. How exactly docker stores the files of an image and a container?
**`Image layer:`** When docker builds images, it builds these in a layered architecture. Docker image layers are read-only. Once the build is complete, you cannot modify the contents and you can only modify them by initiating a new build. 

**`Container top writable layer:`** Once a container is spun from an image, a writable layer gets created on top of the image layer. Writable layer is available in container, but not in image. The writable layer is used to store data created by the container such as application log files, temporary files generated by the container or any files modified by the user on that container. All writes to the container data are stored here and writable layer is deleted when the container gets deleted.

![image](https://user-images.githubusercontent.com/43535914/129486154-b9d77d68-cdca-4d13-9346-4c3304456516.png)


Can’t you modify the file in image layer?

You can modify the file in image layer. But before you save the modified file, docker automatically creates a copy of the file in the read write layer and you will then be modifying a different version of the file in read write layer. All future modifications will be done on this copy of the file in the read-write layer. This is called copy on write mechanism. The image layer being read only just means that the files in these layers will not be modified in the image itself. So the image will remain the same all the time until you rebuild the image using the docker build command.

### 17. Explain image layers?

A Docker image is built up from a series of layers. Each layer represents an instruction in the image’s Dockerfile. Each layer except the very last one is read-only. Each layer is only a set of differences from the layer before it. The layers are stacked on top of each other. When you create a new container, you add a new writable layer on top of the underlying layers. This layer is often called the “container layer”. All changes made to the running container, such as writing new files, modifying existing files, and deleting files, are written to this thin writable container layer. The major difference between a container and an image is the top writable layer. All writes to the container that add new or modify existing data are stored in this writable layer. When the container is deleted, the writable layer is also deleted. The underlying image remains unchanged. Because each container has its own writable container layer, and all changes are stored in this container layer, multiple containers can share access to the same underlying image and yet have their own data state.

### 18. What happens to data of the container when a container exits? How do you persist container data?
By default all files created inside a container are stored in the container itself. The data inside it does not persist (will be lost) when that container no longer exists (Unless of course, you save it as an image first). This is called persistent data problem. But you can add a persistent storage in order to preserve the container’s data.
     
Below are different ways to mount data into a container:
     
- Volumes			--  Stored in the docker managed filesystem (Default location: /var/lib/docker/volumes)
- Bind mounts		--  Stored anywhere on the host file system
- tmpfs Mounts	     --  Stored in the host system's memory 
- External storage     
     
![image](https://user-images.githubusercontent.com/43535914/129486479-3f633502-39e4-4e13-9b9e-bd714a1dcba9.png)

**`1. Volumes:`** Volumes are the persistent data storage used by containers for capturing or saving data beyond the container life cycle. They are written outside the container(ie., on host) and that location is basically mapped inside the container. Irrespective of the fact whether the container is deleted or started again, the new container which is being attached to that volume will have the same file system as that of the older container. When you mount a volume into a container it gets mounted as a directory inside the container. Volume is just a directory possibly with some data in it and which is accessible by containers.

**Ex:**

Consider you run a mysql container and created databases and tables inside it. When you delete a container all the data inside that container will no longer exist. By default, database will stored in location /var/lib/mysql inside a container. In order to persist data you should map a directory on the docker host to a directory inside the docker container using docker volume command like docker -v /opt/datadir:/var/lib/mysql mysql

![image](https://user-images.githubusercontent.com/43535914/129486707-2d9cd7e6-0936-486d-98d1-496aea6c7285.png)

**`2. Bind mount:`** With Bind mount, a file or directory on the host machine is mounted into a container. Can't use Docker CLI commands to directly manage bind mounts.

**Ex:1**

Sharing configuration files, source code or artifacts from the host machine to containers. Suppose we are building our project regularly and container use some new code. So we can replace the jar every time inside the running container without the need of restarting the container again and again. By this way we can share source code or build artifacts between development environment on the docker host and container.

**Ex:2**

If you had data already at another location on host and would like to store container data on that volume and not in the default docker volumes folder.

**`3. tmpfs mount:`** A tmpfs mount is temporary, and only persists in the host memory. When the container stops, the tmpfs mount is removed. If a container is committed, the tmpfs mount is not saved. It is available only with Docker on Linux 

**Ex:** 

Temporary one time password that the containers application creates and uses as needed.

**`4. External (to host) storage:`** Enables data volumes to persist beyond the lifetime of a single Docker host. In case of external volumes even if the docker host goes down the data is not lost. Docker provides volume plugin which can be used for persistent data storage external to the host. While creating the volume using docker volume command we can specify the driver to be used. 

### 19. What is the difference b/w volumes and bind mounts?

Bind Mount | Volume
---------- | -------
Non-docker processes on the docker host can access bind mount and modify them at any time. | Non-docker process cannot modify or access that particular volume inside the container.
Bind mount mounts a directory from any location on the docker host | Volume mount mounts a volume from the docker default volumes directory
Bind mount cannot be used inside a dockerfile because that is not a hard core location on the host machine. | Volume can be used inside a dockerfile.
Can't use Docker CLI commands to directly manage bind mounts. | In case of volumes we have commands like docker volume ls, rm, prune etc.

### 20. Docker command syntax
Docker commands are universal (ie., which ever operating system you use, command remains the same) and case sensitive. Docker management commands are introduced in version 1.13.0

##### Docker management commands format:

    docker <command> <sub-command> <optional-attributes>
command represents management commands like container, image, config, network, volume, swarm, service etc

Sub commands are like execute, run, ls, rm, rmi, info, stop, start, create, etc

**Ex:** Below is the command to run nginx container with name my-nginx in detached mode

    docker container run --name my-nginx -d nginx

##### Note:

Before version 1.13.0, you would simply run commands like `docker <sub-command> <optional-attributes>` although in the new edition as well older commands works fine. 

**Ex:**

Purpose | Old Command | Latest command
------- | ----------- | ---------------
List running containers | 	docker ps |	docker container ls
Run a container | docker run | docker container run
remove an image | docker rmi | docker image rm


### 21. List of Docker commands
<details>
<summary>Info related</summary><br> 

```sh     
# To check Docker version
$ docker -v       (OR)      docker --version      (OR)      docker version

# To list out all the docker commands
$ docker

# Command to display system wide information regarding the Docker installation like the kernel version, docker root directory, storage drivers, number of containers, images, etc
$ docker info
```     
     
</details>

<details>
<summary>Registry/Repository</summary><br> 
Login: 
  
```sh     
# To login to public docker registry(like DockerHub) use the below command and then enter username and password of your DockerHub account
$ docker login     (OR)      docker login -u <username>

# To login to private docker registry(like Harbor)
$ docker login <private-registry-url>
```  
     
Search image:
  
```sh     
# To list all possible repositories in DockerHub where ubuntu images are uploaded.
$ docker search ubuntu
```
     
Pull image:
  
```sh     
# Download specific image (Ex: hello-world) from docker hub (If version is not specified it downloads latest version of image) (We don’t need to login to DockerHub inorder to pull an image)
$ docker pull hello-world:1.1
```
     
Push image:
     
```sh     
# Push docker image to DockerHub
$ docker push <user_name>/<image_name>:<version/tag>
$ docker push <image_name>  --  Will not upload your image since single word image name is allowed only to official images
```
     
Logout:
  
```sh     
# To logout from registry. Always remember to logout from you docker hub account because it stores authorization key in /root/.docker/config.json file. Anyone can use this key and use your account
$ docker logout
```     

</details>

<details>
<summary>Image</summary><br>
List images:

```sh     
# Displays all images present in your machine. Sepcify repo name at the end of command to list images for a specific repository.
$ docker images       (OR)      docker image ls
```
     
Build Image:
     
```sh     
# Build an image from a Dockerfile with speified image name along with tag (If Dockerfile exists in different directory)
$ docker build . -t <username>/<imagename>:<version> -f /path/to/Dockerfile
     
# Build an image from a Dockerfile with speified image name along with tag (If the Dockerfile exists in current directory)    
$ docker build -t <username>/<imagename>:<version> .
```     

Image tagging:
     
Tagging an image means defining version for that image (ie., pointing your image to respective repository by specifying version). This command helps you to tag existing image according to your respective repository. For example, lets say you have an image name my-app. Inorder to push that image to your repository, you have to tag that image according to your repo name like xyz-user/my-app:1.3
  
```sh     
$ docker image tag <image_id> <username>/<Repo_name>:<tag>
```
     
Saving images as tar:
     
Sometimes we may require to copy an image from one machine to another machine. That time we can save an image to a tar file and load the image in another system.
 
```sh     
$ docker save -o <path_for_generated_tar_file> <image_name>
```
     
Load image from tar:
     
Load an image or repository from a tar archive (even if compressed with gzip, bzip2, or xz) from a file or STDIN. Load works with Docker images. Use this command if you want to run an image exported with save. Unlike pull, which requires connecting to a Docker registry, load can import from anywhere (e.g. a file system, URLs).

```sh
$ docker load < /path/to/tar/file
```
                                 
Remove images:

```sh                                 
# You cannot delete an image by simply providing image name as there might exist multiple images with same name. Its always recommended to use image id or complete image name along with its tag. rmi means remove image. docker rmi and docker image rm both commands are one and same
$ docker rmi <image_name>:<tag>     (OR)      docker image rm <image_id>   
     
# To delete multipe images at a time seperate image id's with white space    
$ docker rmi <image_id1> <image_id2> <image_id3>
     
# Deleting an image will not allow to remove an image if some containers whether in running/stopped state are using this image. To Delete an image forcefully, use -f flag. Even after deleting image those referenced containers will still exist, but the image name for that container will be replaced with some random name.
$ docker rmi -f <image_id>
     
# Remove all docker images
$ docker rmi $(docker images -q)     
     
# Remove dangling images: Dangling images are layers that have no relationship to any tagged images. They no longer serve a purpose and consume disk space. 
$ docker image prune --all     
```
         
     
History of an image:

```sh     
# As docker images are constructed in layers, the history command shows these layers, and the commands used to create them. With this command you can view all the dockerfile commands     
$ docker image history <image_id>
```
     
</details>
     
<details>
<summary>Containers</summary><br>
List containers:

```sh
# List out only running containers
$ docker ps
     
# List out all containers (Use -l to show latest container and -q is to get only id of container)
$ docker ps -a
     
# To print only containers names and status
$ docker ps --format 'table {{.Names}}\t{{.Status}}'
     
# To list only exited containers
$ docker ps -a | grep -i Exited

```
     
Create a container:
     
```sh
$ docker container create -it <image_name>
```
     
Start container:

```sh     
$ docker container start <container_id/name>
```
     
Stop container:

```sh     
$ docker container stop <container-id/name>
```
     
Restart container:

```sh     
# Restart one or more containers and processes running inside the container.     
$ docker container restart <container_id/name>
```     
     
Rename container:

```sh     
$ docker container rename <container_oldname> <container_newname>
```         
     
pause/unpause a container:
```sh     
# Pause all processes within one or more containers
$ docker container pause <container_id>
     
# Unpause all processes within one or more containers
$ docker container unpause <container_id>
```      
     
Run a container from an image: &emsp; If image doesn’t exist locally, it will download the image from docker hub. This is only done for the first time. For subsequent executions the same image will be used.
    
```sh     
# Assigns some random name to container as you didn’t specify any name. hello-world is name of the image     
$ docker run -d hello-world
     
# --name flag allows you to specify name for image. (-d runs container as daemon/detach mode in background) (-i interactive mode to make docker container listen to standard input) (-t allocates pseudo-TTY ie., configures terminal)
$ docker run --name test -itd hello-world
     
# Create a container and get inside it ie., accessing container’s terminal.     
$ docker run -it <image_name>:<tag> bash
     
# Configure the container to be self deleted once stopped. It will run a container and delete it immediately after it exits. The --rm flag doesn't work in conjunction with the -d (--detach) flag. When --rm flag is set, Docker also removes the volumes associated with the container when the container is removed.
$ docker run --rm <image-id>     
```
     
Port forwarding:
     
Port forwarding allows communication of container to and from the outside world. It basically publishes port to the outside world by providing external access to your application. This can be done using --publish or -p flag.
     
*Consider you have a simple web app running in a docker container on port 5000. How to access it?*
     
You could access application by using container ip and port 5000. This is internal private bridge network ip and is only accessible from within the docker host.
Users outside of docker host cannot access app using container ip, rather they can access it using host ip. For this to work you must map the port inside the docker container to a free host on the docker host. So other users can access the webapp using host ip and port 80.
If you don’t specify the port number for the host which will be used for routing the communication then docker assigns a random port number. This way you can run multiple instances of an application and map them to different ports on the docker host.
     
```sh 
# External port belongs to host on which container runs and internal port is the port that runs inside container     
$ docker run -d -p <external-port>:<internal-port> <image_name>

Ex:  docker run -it -p 80:5000 --name webapp simple-webapp    -->   You can access the application via browser at URL: http://host-ip:80
```
     
Attach to running container:
     
Attach to a running container, either to view its ongoing output or to control it interactively. Attach isn't for running anything extra in a container, it's for attaching to the running process. Exiting out from the container will stop the container.
     
```sh     
$ docker attach <container_id>
```
     
Execute a new process in an existing container:
     
For logging into/accessing a container (ie., get inside a running container). exec is used run a new process inside the container. Exiting out from container will not stop the container.

```sh     
$ docker exec -it <container_id> /bin/sh
```
     
Exit container:

```sh
ctrl+p then ctrl+q	(OR)    exit	--  To exit the container without stopping it.
```
     
Container hostname:
     
```sh     
# The container host name is set to be same as the container id. You can provide container hostname with the docker run command as showm below.    
$ docker run -it --hostname <host_name> <image_name>
```
     
Copy files/folders between container and host machine:

```sh
# Copy folder from container to host machine (To copy a file specify path till file name to be copied)     
$ docker cp <container-id>:/path/to/folder/ /path/on/host/
     
# copy folder from host machine to container     
$ docker cp ./path/to/folder/on/host/ <container-id>:/path/on/container
```
     
Commit:
     
This is used to commit changes of a container to a Docker image. Lets say you have created a container from an image and later added/modified/deleted few files in that container. The changes will apply only to container and will be lost once container gets deleted. But we can create image out of this container by using docker commit command.      
     
```sh     
# In the below command -m represent message and -a represent author and image_name is the name given to newly created image     
$ docker commit -m “commit_message” -a “abc” <container_id> <image_name>
```   
     
Export:
     
Export works with Docker containers, and it exports a snapshot of the container’s file system.
     
```sh     
$ docker export <container_ID> > <file_name>
```
     
Import:
     
Docker import is a Docker command to create a Docker image by importing the content from an archive or tarball which is created by exporting a container.

```sh     
$ docker import <archive_name> <Image_name>
```
     
Delete container:
     
```sh     
# To delete one or multiple containers. To delete a container it needs to be in stopped state. If not use -f flag to forcefully delete container without stopping    
$ docker rm <container id’s separated by space>

# Delete container along with volumes associated with it
$ docker rm -v
     
# Delete all unused containers
$ docker ps -q -a | xargs docker rm
     
# Remove exited containers
$ docker rm $(docker ps --filter status=exited -qa)     
     
# Delete all containers at once     
$ docker rm -f $(docker ps -a -q)

```
     
Logging:

```sh     
# To check container logs
$ docker logs <container_id/name>

# To check live logs of container. (you can specify -f or --follow)
$ docker logs -f <container _id>
     
$ If you want to check follow up logs of running container     
$ docker logs -f --tail 3 <container _id>
     
# Show running processes in a container
$ docker top <containerName>
```
     
Monitoring and inspection: 

```sh     
# See processes running inside a container from host. There is no need to go inside a container and check     
$ docker container top <container_id>
     
# Provides detailed information about the docker container objects. (Like container ip, volumes, network, etc) (Returns meta data as JSON file)     
$ docker inspect <container_id>
     
# Get resource usage statistics of a container (Like memory usage, resource, performance etc)
$ docker stats <container_id>
```
     
Restrict resource usage of a container:
     
Containers share the same system resources such as cpu, memory etc.(By default there is no restriction). Hence a container may end up utilizing all of the resources on the host. But there is a way to restrict the amount of CPU or memory can container use.

```sh
# Ex: To ensure that container does not take up more than 50% of CPU and 100mb of memory 
$ docker run --cpu=.5 <image_name>
$ docker run --memory=100m <image_name>
```     

kill vs stop:
     
Both will stop running container, but the difference is stop will take 10 sec of time to stop container (First it will send a signal then stops it). Kill wont send any signal it will stop main process in the container abruptly.
    
```sh 
# To kill running docker container     
$ docker container kill <container-id>

# To stop running docker container 
docker container stop <container-id>
```
     
##### run vs start vs exec:     
- Run will create and start a new container always.
- Start will start existing stopped/exited container
- exec is used to execute a command within running container. It only interacts with running containers.
    
</details>

<details>
<summary>Networking commands</summary><br>     

List: &emsp; To view all available networks. 
  
```sh   
# This will provide network id, driver and scope associated to each of these     
$ docker network ls
     
# Format output of list of networks. Similarly you can format output of other commands.     
$ docker network ls --format “{{.ID}}: {{.Driver}}”
     
# To filter all bridge networks     
$ docker network ls --filter drive=bridge
```  
Check network drivers on the docker host.
  
```sh     
# You can see docker0 network interface is listed along with eth0 and loopback interface     
$ ifconfig	(or)	 ip add show
```
     
Inspect network: 
  
```sh     
# Inspect bridge network. Like you can specify any network name or network id     
$ docker network inspect bridge
```     
  
Start container with a network:
     
```sh
# Starts container with host network     
$ docker run -it --network=host <image_name>
```     
     
Connect/disconnet network:   
 
```sh
# Connect existing container to a network     
$ docker network connect <network name> <container id>
     
# Disconnect existing container from a network     
$ docker network disconnect <network name> <container id>
```
     
Create custom network:
 
```sh
# Create new bridge network (new_bridge1 is the name of newly created network)     
$ docker network create --driver=bridge new_bridge1
     
# Create network by specifying subnet and gateway. Internal IP address of containers will be allocated from the specified range. Check ifconfig on host. You can find new network interface added prefixed with br indicating the bridge network followed by the network id. We can also see the ip address provided to this network interface is same as the gateway ip address of the docker network     
$ docker network create --driver=bridge --subnet=172.99.11.0/24 --gateway=172.99.11.1 new_bridge2
```     
     
Remove networks:
    
```sh     
# Note that we cannot delete default networks neither can we delete any network that is being referenced by a container     
$ docker network rm <network-id>
```
</details>     
     
<details>
<summary>Volume commands</summary><br>
Create a volume:
     
```sh     
# This will create a volume folder under /var/lib/volumes/ directory. When you run the docker container using the docker run command, you could mount this volume inside the docker container     
$ docker volume create <name_of_the_volume> 
```
     
List all volumes 

```sh     
$ docker volume ls
```
     
Launch container with volume:
 
```sh     
# Launch container with volume attached using --volume flag. If the volume doesn’t exist it will create one. 
$ docker run -itd --volume <volume-name>:/<mount_path_inside_container> <image_name>

# Launch container with volume attached using --mount flag. 
$ docker run -itd --mount source=<name of the volume>,target=<mount path inside container> <image name>
```
     
Using bind mount:
     
```sh     
$ docker run -itd --mount type=bind,source=<host_path_to_be_mounted>, target=<mount_path_inside_container> <image name>
```
     
Note:
--volume flag can only be used with Docker volumes and not with bind mounts, whereas --mount flag can be used with both.     
     
</details>     
     
<details>
<summary>Cleanup commands</summary><br>
Prune:
     
docker prune is the way to clean up containers, images, volumes and networks on your system.
     
```sh    
# Allows you to clean up unused images. By default, docker image prune only cleans up dangling images. A dangling image is one that is not tagged and is not referenced by any container     
$ docker image prune
     
# Removes all stopped containers     
$ docker container prune
     
# Remove all unused local volumes     
$ docker volume prune
     
# Remove all unused networks
$ docker network prune
     
# It is used to remove all the stopped containers, all the networks that are not used, all dangling images and all build caches
$ docker system prune
```
     
</details>
    

### 22. Dockerfile
Dockerfile is a text document that contains a series of instructions paired with arguments. Each instruction should be in uppercase and instructions in the Dockerfile are processed from top to bottom.

**`How to name Dockerfile:`** &emsp; The default filename is Dockerfile (without an extension), and using the default can make various tasks easier while working with containers. But you can name Dockerfile with any name like Dockerfile.dev, Dockerfile.prod, etc.   
     
##### Dockerfile instructions:

Command | Syntax | Description
------- | ------ | -----------    
FROM | FROM \<image\>:\<tag\> | Defines the base image for building a new image. Docker file must start with FROM instruction. Can be used multiple times in a dockerfile.
LABEL | LABEL key=”value” | Adds metadata to an image (like project, version, licensing information etc). It is a key-value pair.
MAINTAINER | MAINTAINER email | Allows to set author field for the generated images. Define the name and email address of the image creator.
ENV | ENV key=value | Used to set the environment variables which can be accessible within the container by scripts and applications alike.
USER	| USER \<username\> | Set the UID (or username) to use when running image.
RUN | RUN \<Executable_commands\> | Executes command in a new layer on top of the current image and commits the results. Executes a Linux command to install, configure etc.
ENTRYPOINT | ENTRYPOINT ["executable", "paraml", "param2"] <br> (OR) <br> ENTRYPOINT command param1 param2 | Allows you to configure a container that will run as an executable. Sets the default application that is used every time a container is created. 
CMD | CMD [“executable”,”param1”,”param2”] <br> (OR) <br> CMD command param1 param2 | The main purpose of a CMD is to provide defaults for an executing container. If Dockerfile has more than one CMD instruction then only the last one will get executed. 
EXPOSE | EXPOSE \<port\> | Informs docker that container listens on the specified port at run time.
WORKDIR | WORKDIR \<Path\> | Sets the working directory for any RUN, CMD, ENTRYPOINT, COPY and ADD instructions that follows it. If a relative path is provided, it will be relative to the path of previous WORKDIR instruction.
VOLUME | VOLUME /path/on/host | Creates a mount point with the specified name and marks it as holding externally mounted volumes from the native host or other containers.
COPY | COPY \<src\> \<dest\>	| Lets you copy files or directories from host into the filesystem of container 
ADD | ADD \<src\> \<dest\> | Copies files, directories, remote file URL’s or compressed file from source and adds them to the file system of the image at specified destination path.

Below is the sample Dockerfile that runs simple web application in Tomcat.
     
    FROM ubuntu
    MAINTAINER abc@gmail.com
    LABEL com.example.version=”0.0.1-beta”
    LABEL vendor=”ACM”
    RUN apt-get update
    RUN apt-get -y install apache2
    ADD ./index.html /var/www/html
    ENTRYPOINT apachectl -D FOREGROUND
    ENV name test

     
### 23. What is .dockerignore file?     
It allows you to specify a pattern for files and folders that should be ignored by the Docker client when generating a build context.     
Before the docker CLI sends the context to docker daemon it looks for .dockerignore file in the root directory. It exclude files and directories that match patterns in this file. This helps to avoid unnecessarily sending files and directories to the daemon.

**Ex:**  .dockerignore file contain patterns like below:
     
.*		README*		*.yaml

     
### 24. What are the best practices related to working with containers or Dockerfile?
- Specify Image Tags for base image you use
- Reduce build context: Build context is a set of files at either local path (directory on your file system) or a URL (git repository location) in the Dockerfile folder. When a build is run by Docker, first thing it does is send the Dockerfile and the entire context (recursively) to the daemon. When you issue a docker build command, the current working directory is called the build context. By default, the Dockerfile is assumed to be located here, but you can specify a different location with the file flag (-f). Regardless of where the Dockerfile actually lives, all recursive contents of files and directories in the current directory are sent to the Docker daemon as the build context. The best way is to put the Dockerfile inside the empty directory and then add only the application and configuration files required for building the docker image.
- Use a .dockerignore file: To increase the build’s performance, you can exclude files and directories by adding a .dockerignore file to that directory as well.     
- Avoid installing unnecessary packages
- Minimize the number of layers: Each instruction in the Dockerfile adds an extra layer to the docker image. The number of instructions and layers should be kept to a minimum as this ultimately affects build performance and time.
- Sort multi-line arguments: Sorting multiline arguments alphanumerically will help avoid duplication of packages and make the list much easier to update.
     
      RUN yum update -y && \
          yum install -y apache2 \
                         git \
                         java
                     

### 25. What is the differnce between CMD and ENTRYPOINT Docker instructions?     
CMD sets default command and/or parameters, which can be overridden when command line parameters are passed when a docker container runs (CMD will be executed only when you run container without specifying a command/parameters), where as in case of ENTRYPOINT the command line parameters will get appended. In short, command and parameters of ENTRYPOINT are not ignored when Docker container runs with command line parameters.      

Example of CMD:
     
Lets say, in Dockerfile you have CMD like: 
     
    CMD echo "Hello world"

when container runs as docker run -it <image> the output will be like:     
     
    Hello world
    
When container runs with a command, e.g., docker run -it <image> /bin/bash, CMD is ignored and bash interpreter runs instead:      
     
    root@7de4bed89922:/#

Example of ENTRYPOINT:
    
Lets say, in Dockerfile you have CMD and ENTRYPOINT like 
    
    ENTRYPOINT ["/bin/echo", "Hello"]
    CMD ["world"]
     
when container runs as docker run -it <image> will produce output
     
    Hello world
    
when container runs as docker run -it <image> John will result in
     
    Hello John
    
You can also override the default executable by using the --entrypoint flag while running the container. When container runs as docker run -it --entrypoint /bin/bash <image> then the output will be as shown below
     
    root@7de4bed89922:/#  
 
     
### 26. What are multi-stage builds?
With multi-stage builds, you use multiple FROM statements in your Dockerfile. Each FROM instruction can use a different base, and each of them begins a new stage of the build. For longer Dockerfiles, or just for clarity you can name the stages of the build using the AS command. You can selectively copy artifacts from one stage to another, leaving behind everything you don’t want in the final image.
Multi-stage builds allow you to drastically reduce the size of your final image, without struggling to reduce the number of intermediate layers and files.     

**Ex:**  
     
     FROM node:14 AS sass
     WORKDIR /example
     RUN npm install -g node-sass
     COPY example.scss .
     RUN node-sass example.scss example.css

     FROM php:8.0-apache
     COPY --from=composer:2 /usr/bin/composer /usr/bin/composer
     COPY composer.json .
     COPY composer.lock .
     RUN composer install --no-dev
     COPY --from=sass /example/example.css example.css
     COPY index.php .
     COPY src/ src


### 27. Explain about Docker-compose:
Docker-compose is a tool for defining and running multi-container docker applications. In case of applications which follow micro services architecture you have multiple layers each providing a specific service. Each layer would have a different container running thereby making your application a multi-container application. Running one container at a time and configuring the required dependencies between the different layers would be difficult to do manually. For such purpose docker compose is useful. 
     
In short, With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.

For example, you can use it to set up ELK stack where the services are: elasticsearch, logstash and kibana. Each running in its own container.     
     
How to use docker compose:
With compose you use a YAML file to configure your application services. In YAML we define services (basically the individual containers), networks, volumes required for our complete application to run. Once the compose is defined, with a single command (docker-compose up) you create and start all the services from your configuration.

Docker-compose YML file:

1.  If you create YML file with default name  --  docker-compose.yml
Run docker-compose up command to bring up the entire application stack. 
docker-compose down  --  To bring down entire services

2.  If you provide custom name for YML file like xxx.yml then you can execute your docker compose file with the command
docker-compose -f xxx.yml up -d
 

### 28. What is container orchestration?
As the scale of operation increases it becomes nearly impossible to manage the entire infrastructure. Therefore the need of the orchestration arises. It provides automated configuration, coordination, and management of the backend servers, which collectively provide a Service. Container orchestration is the process of deploying and maintaining large number of containers and services for the application to run as intended. 

Important responsibilities of Orchestration tools are:
     
-  Provisioning and deployment
-  Scaling up or down the containers.
-  Allocation of resources
-  Health monitoring (check availability of containers)
-  Movement of containers from one host to another in case of any issues with host or during maintenance cycles

Few popular orchestration Engines are - Docker Swarm, Kubernetes and Apache Mesos/Marathon     
     
### 29. What is Docker swarm?
Multi-container, multi-machine applications are made possible by joining machines into a dockerized cluster called as swarm. Docker swarm is a container orchestration tool, part of the docker engine. A swarm is a group of machines that are running docker and joined into a cluster. After joining a swarm they are referred to as nodes. Docker swarm allows you to deploy and manage a cluster of docker nodes (each of which running several container instances) as a single virtual system.
     
Note:
Docker swarm is basically idle for small scale applications. For large scale applications we prefer kubernetes.     
     
### 30. Difference between docker compose and swarm
Docker Swarm runs multi-container applications, just like Compose does. The key difference is that Swarm schedules and manages your containers across multiple machines, while Compose schedules and manages containers on a single host only.     

### 31. Explain Docker swarm architecture?

![image](https://user-images.githubusercontent.com/43535914/129487616-e7b793c6-b708-408b-a01c-302aeb13bec6.png)

Service        --  Define tasks that needs to be executed on the manager and worker nodes. Service defines how the particular application will work, what its task is
     
Task           --  Task refer to the docker containers that execute the commands defined in the service. (Ex: You have a service with 3 nginx replicas then you will have several worker nodes which will perform these tasks)
     
Manager node   --  It manages all worker nodes. Manager node is responsible for:
     
- Accepting commands and creating service object
- Allocating IP addresses to tasks
- Assigning tasks to nodes
- Instructing a worker to run a task.
     
Worker node    --  They are responsible for checking assigned tasks and executing them.     
     
### 32. Commands to build a docker swarm     
Initializing a swarm with manager:

    docker swarm init --advertise-addr <manager-ip>  --  Initializes docker swarm with a manager. Any other node that gets added to this particular swarm becomes worker node. 

When you initialize manager node for first time a token will be generated. If you want to view worker join token again then use 

    docker swarm join-token worker

Adding a worker to a swarm:

    docker swarm join --token <token_id>  --  Used to join a node into swarm as a worker.

Check swarm state:

    docker info  --  To get information about swarm
    docker node ls  --  Gives you list of connected nodes (Use this command from manager node)

Exiting the swarm: These commands can be used from the node terminal to leave a swarm.

    docker swarm leave		(OR)		docker swarm leave --force   

Remove a node: This command can be used in a manager node terminal to remove a node.     

    docker node rm <node-id>	(OR)		docker node rm -f <node-id>
     
     
