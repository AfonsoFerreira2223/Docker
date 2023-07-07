
# What is docker and why use it (by someone who is trying to figure out what is docker and why use it):


### Disclaimer: This is the first time I am working on docker. Take any information here with a grain of salt.

Docker uses containers- These are isolated environments to run an application.

Containers work similarly to VMs. They are lightweight software packages that encapsulate an application and dependencies, so they it can run consistently across different computing environments. They are lightweight, fast, and can be pushed to docker hub for instant access on any machine.

Think of a virtual machine and a container like boxes. The VM is a big box, it can store loads of information but it also heavy and takes lots of space. Containers are small boxes, made for specific items, whihc makes them easier to find and store, or bring them with you anywhere.

Containers are treated like any other process running on your computer. 

They can be runned using an image.

They use the same Kernel as the host system, unlike Vms, they don’t run on their own OS.


Docker may be preferable to a VM as the latter requires more resources, is slower to start and needs a full blown OS.


# Installing docker on ubuntu:

This project was made using a machine on aws running ubuntu.


The commands to install docker on an ubuntu distro are:

```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
apt-cache policy docker-ce
sudo apt install docker-ce
```

If you now run sudo ```systemctl status docker``` it should show an output simmilar to this:

![image](https://github.com/AfonsoFerreira2223/Docker/assets/114146560/8bf021fe-1655-4e7b-aa86-2a1184e5e0f9)



**Instaling docker gives you the docker daimon (server) and the command line uttility (client)**


The Docker daemon is the background service that manages Docker containers and other Docker components, while the Docker client is the command-line utility that allows you to manage Docker containers.


You can start by testing dockers's most famous container:


```
docker run hello-world
```

The output should be something like this:

```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
0e03bdcc26d7: Pull complete
Digest: sha256:6a65f928fb91fcfbc963f7aa6d57c8eeb426ad9a20c7ee045538ef34847f44f1
Status: Downloaded newer image for hello-world:latest
```

Docker cannot find the immage hello-world stored locally, so it will look it up on docker hub.

After downloading the image, docker will create a container based on that image.

And finally show you the content of that container with the run command.

Try to run ```docker run hello world``` once again


![image](https://github.com/AfonsoFerreira2223/Docker/assets/114146560/995b0b4e-e1bc-45b3-8da1-554ac6e20bef)


Tip: Sudo su will take you directly to root, since docker requires high-level permissions to run most of its commands.


# Pulling images from docker:

You can pull images from docker hub 

```
docker pull ubuntu
```

This will get you an image from a basic ubuntu cli avaible on  docker hub.

You can run ```docker images``` to see the images stored on your computer


Now to run a container based on this ubuntu image:
```
docker run -it ubuntu
```

this will start the ubuntu machine container, and you can now issue commands just like in the host machine

for example, installing netcat:

```
apt update
apt upgrade
apt install netcat
```

issue the command ```exit``` to return to your host machine.
