---
toc: true
layout: post
description: A general introduction to the Docker echo system. The ideas and terminologies. On what Docker is, and how it functions from a conceptual level. How is useful to the modern developer.
categories: [docker, devops]
title: Enter the World of Docker
comments: true
---

# Introduction
The idea of having an isolated environment is nothing new. To keep your computer clear of all clutter which is produced by installing programming language, framework, and databases. This is something you worry about when you have passed the beginning of your programming journey. There always have been solutions for you to achieve this in the modern programming paradigm. But as programming evolves and get's better. So does the tool to help you write programs.

## World before Docker
In the past, we had solutions that would introduce a complete virtual environment. This will be an isolated OS on your system with its operating system, fixed and expendable resources. This was a viable solution, and it is still used in some case studies these days. But most of us don't need such a resource hugging solution. Anyone that has run something like [Virtualbox](https://www.virtualbox.org/) or similar solution would know what I mean. We also had solutions like [vagrant](https://www.vagrantup.com/). But they also had their problems of being efficient you can read up more on them on the internet. I personally had worked with Virtualbox and found it much easier to work with than Vagrant. But I might have had been a younger develop back than. But that should speak volumes for its developer-friendly nature.

## World with Docker
Enter Docker. So how has the world changed? Docker allows the users to use the underline kernel of the OS and just isolate the parts of the application that is unique. This greatly reduces the resources intensive nature of virtualization, with some additional perks. You can mimic your development environment without worrying about the machine you are developing on. It also lets you pass around your environment with your team and they can start off with a similar environment instantaneously. It is also helpful for getting the junior and new recruits without letting them worry about setup.

# What is Docker?
Docker is exactly like a virtual environment. But the much more appealing as compared to a VirtualBox solution. It lets you use the kernel of your base operating system. Since you already have it installed. If you are using a Windows or Mac OS. you will have install the docker with the lunix container system to access to kernel. That is done automatically for Docker Desktop installation on either OSs. But in Linux you don't have to install the Linux kernel. Since it is already part of the operating system. Docker has some key terminologies. Knowing them will be helpful on your learning journey.

1. Images
2. Containers
3. Volumes
4. Networks


## Images
This is the core of your application. Just like when you are deploying an application to a server. You have to get hosting from AWS, or Azure. You select your VM (virtual machine), and select a Linux flavor. If it is a Linux server? (Docker works with windows based images as well.) Then you install all of your required programming languages and tools (databases, queueing system, etc.). An image is that isolation in Docker. You can backup your VM and spin-up other VMs with it. The same concept applies to images in docker. You can use an image to create multiple containers. An image in Docker can be ubuntu, fedora, or alpine based. I will talk more about my choice of Linux version Alpine in the series of Docker posts.

## Containers
Following along the same analogy of VMs. When you have the VM configured and installed all of your application dependency. Know that code of your application has to be pulled in to the VM and some configuration has to be made for it to run on the VM. This running of your application is equal to a  container in the Docker universe. What Docker lets you do is to encapsulate your code into the container.

## Volume
When you run a container all of your application's state is stored in the container. If you remove your container all the files in that container will be removed. What this means is that, if your application has uploaded images or files within the container. They will be removed along the container. Also, when you have a database running as a container, all of your databases active will be removed with the container. This is scary. But don't worry. Docker lets you mount a folder on to your system to the inside of a container. The mouning syncs the files and folder between the folder on your computer with the container. You lose no information. Know if you remove the container, or even the image, your data is safe and sound. When you recreate the container you can carry on from where you have left off. Pretty cool right?

## Networks
Since Docker is its own light computer running inside your VM or the local machine. It maps its ports for communication to the outside world. For the ports to be accessable externally from the container, we have to do that in the configuration. It is part of the Docker configuration process. You can create a network within Docker that will help your container communicate on a shared resource machine(everything running on the same machine). You can also create an overlay network in docker that spans over multiple machines. 

## Docker and its files
So how does the alchemy of Docker works? Well, it is quite simple if you understand the key points of Docker. Since the docker entire creation process is working with config files. You don't need programming for the most part of working with Docker. Two key config files that you work are defined as follows.

## Dockerfile
A file name `Dockerfile` with no extension is where you create the image. refer to the [Image](#Images) heading. You can have a different name. The Dockerfile is just the default format. If you choose to have a different name, you need to specify the filename when you are running the Docker commands.
  
## Docker-compose
Everything in Docker is an individual image. Databases, programming language, frameworks, etc. They function independently. If you want to run multiple images an example would be python running on alpine Linux base image, using Django as the web backend framework, Postgres, or MySql as a primary database, Redis as a caching database, and a job scheduler. You can define all of them in the `docker-compose.yml` file. The extension of this file can be `YML` or `YMAL`. It does not matter which extension you use. Whatever you specify in the docker-compose file will be on the same network. You don't need to link them manually. But if you choose for it to be part of a predefined network. Or let other containers connect with the resources created by a docker-compose file you can do that within the docker-compose file.
> Always remember to use the internal ports when you have created a connection. Since all of them are on the same network. You can use the service name instead of an IP as your host. This will help you in case if you recreate a container, the IP will be taken care of by Docker.

# Conclusion
In future posts, I will talk in-depth on how to work with each aspect of the Docker environment. I will dedicate a post for each of the main ideas in the Docker environment. If you have any question comment below or feel free to [email me @](mailto:admin@abdulwahidgul.me)
