# DevOps

- [Terraform]
  - [🚀Link to terraform repository](https://www.github.com/jojo-tey/terraform)
- [Docker](#Docker)
  - [Interview Questions for Docker](#Interview-Questions-for-Docker)
  - [Why Docker?](#Why-Docker?)
  - [Virtualize](#Virtualize)
  - [Container and Image](#Container-and-Image)
  - [Dockerfile](#Dockerfile)
  - [Docker Hub & Docker Registry](#Docker-Hub-&-Docker-Registry)
  - [Docker and Docker-compose](#Docker-and-Docker-compose)
- [Kubernetes]
  - [What is Kubernetes?](#What-is-Kubernetes?)
  - [Kubernetes workflow](#Kubernetes-workflow)
  - [Kubernetes components](#Kubernetes-components)
  - [Kubernetes and Docker-compose](#[Kubernetes-and-Docker-compose])
- [Jenkins](#Jenkins)

## Interview Questions for Docker

* [Docker Interview Questions](https://mindmajix.com/docker-interview-questions)
* [Top Docker Interview Questions You Must Prepare In 2019](https://www.edureka.co/blog/interview-questions/docker-interview-questions/)
* [Top Docker Interview Questions And Answers](https://intellipaat.com/interview-question/docker-interview-questions/)
* [DOCKER (SOFTWARE) INTERVIEW QUESTIONS & ANSWERS](https://www.wisdomjobs.com/e-university/docker-software-interview-questions.html)
* [30 Docker Interview Questions and Answers in 2019](https://www.fullstack.cafe/blog/docker-interview-questions-and-answers)

## Docker

> Docker is an open source virtualization platform based on a Linux container written in Go language

### Why Docker?

  1. To secure an unchanging execution environment

  2. Execution environment construction and application configuration through code

  3. Improved portability by unifying the execution environment and application <br>

In other words, you can configure the same environment without change while developing the application. <br>
Even if the same application is running, the environment is different for each server for each user. You can make this problem in the same execution environment with Docker.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)

### Virtualize

From the server administrator's point of view, it is inevitably a waste of resources for underutilized servers with only 10% CPU usage. However, if you put all the services in one server, there may be a problem with stability. That is why server virtualization has emerged as a way to increase stability and make the most of resources. The representative virtualization platform that everyone knows is VM. VM is an OS virtualization that everyone knows. So what is a container?

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)

### Container and Image 

- Container <br> 

Container is one of the virtualization technologies, typically LXC (Linux Container). Unlike existing OS virtualization, the container operates by isolating processes through OS-level virtualization.<br>
What is the difference between virtualizing and using multiple OSs on one server and how to isolate and operate processes in a container way?

![Image](/images/virtualize.jpg)

In the case of VMs that are familiar to us in the past, we use a hypervisor engine for virtualization on top of the host OS and a guest OS on top of it. It is safe to say that it is almost completely separated from the host in the form of an OS on top of virtualized hardware. On the other hand, in container-based virtualization, only the binaries required to run the application are on top of the Docker engine. OS virtualization has the advantage of being completely separated from the host OS, but it is inevitably heavy and slow because it puts the OS on top of the OS. However, container-based virtualization runs directly on the Host OS and Docker engine and shares the host's kernel. If the kernel is shared, io processing becomes easier and performance efficiency can be improved. <br>

Using containers does not create virtual machines, but rather separates the resources used by the Host OS so that multiple environments can be created.
<br>
 
It seems to say that container-based is better than OS virtualization, but it is not. <br>
As this is an introduction to Docker, I emphasized the advantages of container-based virtualization compared to OS virtualization, and explained why Docker is used.<br>

OS virtualization supports a higher level of isolation than container-based virtualization. This is more advantageous in terms of security.
It also has the advantage of not sharing the kernel of OS virtualization. As long as the kernel is not shared, multiple OSes are possible. The fact that multi-OS is not possible because the kernel is not shared has the disadvantage of not being able to load Windows on Linux. Nevertheless, I think the reason why Docker is used is performance improvement, excellent portability, and flexibility to scale out easily.



- Image <br>
The file system that makes up the container and the settings of the application to be run are combined into one. Template for creating a container

![Image](/images/dockerimage.png)

You can think of a Docker Image as having an executable file and configuration values that can run a container. <br>
As shown in the figure, if you put an Image in a container and run it, the corresponding process will run. <br>
So, in order to know how to make an image, let's first look at how an image is made.


![Image](/images/dockerimage2.png)

Looking at the following picture, Layers A, B, and C are added to make ubuntu image. So what if you thought you were making an nginx image? <br> Using the Ubuntu image already made in Layers A, B, C as the base image, only nginx is added to the base image. If so, Layers A, B, C, and nginx are actually added, but the process is unbuntu + nginx. So what happens when you try to create a web app image? Instead of uploading nginx to the ubuntu image and uploading the web app, you will create an image by uploading the web app to the already created nginx base image. <br>
Now that you know how an image is created, let's take a look at the Docker File that actually creates an image.


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)


### Dockerfile

Docker Hub, which stores and distributes Docker images, is really well activated. Several companies have already started distributing software through Docker Hub, and we can simply pull images from Docker hub and use them in containers. But this seems to be lacking in something. What if there is no distribution? Would you like to complement it more than the distribution? Docker Fille is what you can use in that case. <br>
Docker File is the starting point for image creation, and you can compose an image by writing commands to compose the image. That means if you can read the Docker File, you can also know how the image is organized.

```
# Example


FROM python:3.8-alpine

ENV PATH="/scripts:${PATH}"

COPY ./requirements.txt /requirements.txt 
RUN apk add --update --no-cache --virtual .tmp gcc libc-dev build-base linux-headers python3-dev
RUN apk add --no-cache jpeg-dev zlib-dev

RUN pip install -r /requirements.txt
RUN apk del .tmp

RUN mkdir /app
COPY ./app /app
WORKDIR /app
COPY ./scripts /scripts



RUN chmod +x /scripts/*

# access permission for user
RUN mkdir -p /vol/web/media  
RUN mkdir -p /vol/web

RUN adduser -D user
RUN chown -R user:user /vol
RUN chmod -R 755 /vol/web
USER user

CMD ["entrypoint.sh"]
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)


### Docker Hub & Docker Registry

- Docker Hub stores and manages images. Above, many companies have started distributing software with Docker, and public images can be shared. With Docker Hub, you can easily pull an imaer and apply it to a container. (In fact, it doesn't matter if you think the same as GitHub) <br>

> Then what is the Docker Registry?

You can build privately isolated storage rather than openly like Docker Hub.

![Image](/images/docker-regi.png)

This is the url to pull the Docker Image. As shown in the picture, if you do not write the url in front, the image will be pulled from Docker Hub by default, and if you write the url, you can receive the image from private storage.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)

### Docker and Docker-compose

Typical systems do not run as a single application. A system consists of several applications that depend on each other. If so, it is often said that one container is responsible for one application, and you need multiple containers. The required skill at this time is Docker Compose. Docker Compose is written in yaml format and allows you to manage the execution of multiple containers at once.

```
# Example

version: '3.8'

services:
  django_gunicorn:
    volumes:
      - static:/static
      - media:/media
    environment:
      - SECRET_KEY=${SECRET_KEY}
    build:
      context: .
    ports:
      - "8000:8000"
  nginx:
    build: ./nginx
    volumes:
      - static:/static
      - media:/media
    ports:
      - "80:80"
    depends_on:
      - django_gunicorn
      
volumes:
  static: 
  media:

```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)

<br>

## Kubernetes

### What is Kubernetes?


- Kubernetes is a portable, extensible open source platform for managing containerized workloads and services
- Kubernetes facilitates both declarative configuration and automation

![Image](/images/kubernetes.png)


1. Scalability <br>
It's easy to scale, because Kubernetes is designed according to the experience of running billions of containers a week to live up to the reputation of being made by Google.

2. Flexibility <br>
Regardless of the environment, whether it is local testing, product operation, or environment, it has the flexibility to accommodate all the complex needs of users, so users' applications can be delivered endlessly and easily.

3. Portability <br>
Kubernetes is open source and runs in multiple environments, whether on-prem, hybrid, or public cloud infrastructure.
Kubernetes has many other advantages and features, but it has very simple logic. 

>A simple rule of 3 steps that monitors the current state and changes it to the value set by the administrator if it is different from the value set by the administrator. Therefore, the administrator does not manage with commands, but manages with yaml files containing the set values.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)

### Kubernetes workflow

![Image](/images/kubernetes-node.png)

Usually, it will be different for each organization, but the partner company or the collaboration department forwards the request for the service to the manager. <br>
The manager passes this command to the Master Node, and Master Node distributes traffic while delivering commands to Worker Nodes.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)

### Kubernetes components


![Image](/images/kubernetes-diagram.png)


#### Master Node

As the main control unit of Kubernetes, it is the entity that manages Worker Nodes. It is responsible for making overall decisions about the cluster and detecting and responding to events. <br>

- Kubectl <br>
A command to communicate with the master node, which uses the Kubernetes API to interact with the master node.
- API Server<br>
Responsible for handling REST API requests and communicating with each of the components that make up the Kubernetes cluster.
- Scheduler<br>
A role that checks the resource status of nodes and selects the appropriate node where the pod will be placed.
- Controller Manager<br>
The role of monitoring the state of the Kubernetes cluster and keeping it configured.
- ETCD<br>
As an open source key-value storage, in Kubernetes, API Server of Master Node is used to store configuration data that can be accessed using HTTP/JSON API.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)

#### Worker Node

Worker nodes are systems that perform assigned tasks as requested.
In the past, it was also called Minions, and it communicates with the master node to perform overall tasks necessary for services such as network between containers. <br>

- Kubelet<br>
As an agent in charge of communication between Kubernetes master nodes, it manages pods running on nodes.
- Kube-proxy<br>
Mounted for each node and acts as a network proxy and load balancer.
- Pods<br>
Pods are groups of containers, a Kubernetes unit of work that contains one or more containers.


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)


### Kubernetes and Docker-compose

- Docker-compose declares the container when I start it. There is no concept of node or cluster
- Docker Compose is a tool for defining and running multi-container Docker applications without orchestration
- Kubernetes has the concept of pods, which have multiple containers and allow the concept of distribution (clustering) between available nodes

> However, both can create configuration files (Yaml). Probably for this reason, it seems to be causing confusion in the relationship between the two


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)


## Jenkins

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)