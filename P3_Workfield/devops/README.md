# DevOps

- [Terraform](https://www.github.com/jojo-tey/terraform)
  - [🚀Link to terraform repository](https://www.github.com/jojo-tey/terraform)
- [Docker](#Docker)
  - [Interview Questions for Docker](#Interview-Questions-for-Docker)
  - [Why Docker](#Why-Docker)
  - [Virtualize](#Virtualize)
  - [Container and Image](#Container-and-Image)
  - [Dockerfile](#Dockerfile)
  - [Docker Hub and Docker Registry](#Docker-Hub-and-Docker-Registry)
  - [Docker and Docker-compose](#Docker-and-Docker-compose)
- [Kubernetes](#Kubernetes)
  - [What is Kubernetes?](#What-is-Kubernetes?)
  - [Kubernetes workflow](#Kubernetes-workflow)
  - [Kubernetes components](#Kubernetes-components)
  - [Kubernetes and Docker-compose](#Kubernetes-and-Docker-compose)
- [Jenkins](#Jenkins)
  - [Why Jenkins?](#Why-Jenkins?)
  - [Jenkins Advantages and Disadvantages](#Jenkins-Advantages-and-Disadvantages)
  - [Jenkins automation](#Jenkins-automation)
  - [How Jenkins works](#How-Jenkins-works)

## Interview Questions for Docker

* [Docker Interview Questions](https://mindmajix.com/docker-interview-questions)
* [Top Docker Interview Questions You Must Prepare In 2019](https://www.edureka.co/blog/interview-questions/docker-interview-questions/)
* [Top Docker Interview Questions And Answers](https://intellipaat.com/interview-question/docker-interview-questions/)
* [DOCKER (SOFTWARE) INTERVIEW QUESTIONS & ANSWERS](https://www.wisdomjobs.com/e-university/docker-software-interview-questions.html)
* [30 Docker Interview Questions and Answers in 2019](https://www.fullstack.cafe/blog/docker-interview-questions-and-answers)

## Docker

> Docker is an open source virtualization platform based on a Linux container written in Go language

### Why Docker

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

### Why Jenkins?

A common problem with many devops teams is a fragmented workflow. Most of the time, they get angry at inefficient work. <br>
Team members tend to work independently. With solo coding, engineers regularly generate large amounts of code outside of version control. When the developer is "done," he adds the task to the base code. Then another team manually runs tests to verify the build.<br>
Over the years, many teams have found this division of labor to be cumbersome and problematic.<br>
Larger version control changes by multiple developers individually leads to complex bugs, increases time-consuming fixes, and increases the time it takes to perform more manual tests. Everything slows down.<br>
This shortens build cycles, shortens production time, and ultimately lowers your company's bottom line with tedious debugging.<br>

#### What does continuous integration mean? 

- CI (Continuous Integration) is a process aimed at reducing build cycle inefficiencies by allowing developers to compile their team's code from a shared version control repository. CI allows you to automate your tests, so you can set up your system to automatically run unit tests or integration tests, for example.<br>

- CI automatically monitors each engineer's commit. This simplifies writing and validating your code so your tests don't get much attention. It is recognized as a best practice in the software development community.<br>

- CI runs on a shared server that increases visibility, so every engineer in the project will be aware of changes to the underlying code on a daily basis. You can also configure the server to alert developers when submitting failed code so they can fix server errors.<br>

- CI automation can shorten development release cycles and improve product quality. CI essentially empowers teams to use machines to do their best, so people can bring more value to your company. It can also be customized both to fit your project and needs.<br>

- CI environments can provide different levels of test automation.<br>

- A CI/CD server with Jenkins allows you to set up the tests your team needs to run.<br>

- There are different levels of testing that can be implemented. The most basic test is whether the code actually compiles. Code can be "lint" or style checked. Teams can write more complex tests that cover different bases, including unit, integration, stress, regression tests, and more.<br>

#### How is Continuous Integration different from Continuous Delivery?

- The CI service compiles and tests the entire application. In addition, continuous delivery pushes this tested application to the repository so that, for example, alpha testers can use and provide early feedback. CD builds are automatically deployed into production environments and can also be used for extensive beta testing.<br>

- CD aims at Lean Logistics. Automate the process from adding new code to acceptance testing. The CD is ready to deploy the build by automating every step.<br>

- Continuous delivery: In addition to building applications and running tests, applications are also "delivered". This often means placing it on a server so that someone can perform manual tests, or emailing it to users in the test group.<br>

- For production builds, delivery means deploying the application for end users. This allows products to be deployed faster and on a smaller scale, reducing the risk of deployment. Regular small and concise deliveries are less risky than large deliveries that occur only once or twice a year.<br>


#### How does Continuous Integration / Delivery help your development team?

- Many people talk about CI as it is considered best practice to automatically check all code on every commit for the reasons mentioned above, run tests regularly and deploy continuously.

- The process makes sure that each developer's contribution works well together. The early detection of these issues makes it easier and faster to fix bugs.

- As you can guess, implementing a CI/CD will bring about a cultural change to your team. It becomes more agile and integrated.

- CI was created to ensure that teams don't waste time manually resolving conflicting new code segments, triggering builds, or running tests. Instead, I recommend adding small incremental changes to your code to avoid getting huge and complex bugs to fix. This can speed up build cycles, streamlining deployment and production.

- Also, production is where the business really makes money.

- Also interestingly, for a multi-developer remote team, CI is very useful to implement because it puts all the work together and continuously combines them, regardless of geographic location, to keep all the work the same.

- When you run Jenkins, you can run a set of basic tests that you programmed to constantly check if your code compiles and check the base code after every commit.

- The merged code can be automatically deployed to the integration environment and used for manual testing.

- You also use it to create and deploy production builds. Deployment is complicated because you don't update a single system. You are updating the entire system cluster. Updates should be done in a way that does not interfere with the service. Deploying in such an environment can cause errors if humans do


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)


## Jenkins Advantages and Disadvantages

##### Jenkins is an old tool with an unfamiliar user interface.

- The good news is that the Jenkins project has just released Blue Ocean, a continuous delivery software designed to significantly improve the UI. It is 100% open source.

- When your team considers the option of continuous integration, Jenkins needs to run on a server (cost) and sometimes needs the attention of someone with systems management skills (time). After setting up the system, you can't expect it to run on its own, you need to update and maintain the system frequently.

- However, Jenkins is open source and is one of the most widely used and most used free tools to implement CI/CD for a team of developers.

- The barrier to entry for most teams is initial setup, delay, or failure to attempt previous setup. People know this is the best way to do it, but many teams ignore it for more urgent coding work. Perhaps someone on the team tried to implement Jenkins at some point, but it wasn't successful. Maybe the wasted effort left your boss badly impressed.

##### The reason people don't implement a CI server is usually very practical.

- One main reason: CI system goes down regularly. When a project's settings change, it is often necessary to re-adjust the configuration of the CI system. If a CI system is not perceived as of high value by the team, it tends to put the CI system aside and thus stops providing value.

- Another reason not to use CI is that you have to write tests. Unit testing is something most developers want to do (e.g. best practices), but they often don't find time to do it. Naturally, coding real software is a business priority over more administrative tasks.

- In addition, the test is interrupted, so if the function being tested changes, it must be updated. If not updated, the value offering will cease as above. You need to prioritize infrastructure maintenance. Otherwise it won't work.

- In short, it takes time to set up and requires a fair amount of work to keep it updated. However, teams can test to simplify system maintenance and increase efficiency.

- Of course, the SaaS alternative to Jenkins is hosted, so it can help if someone else pays a little extra to maintain the software. Enterprises tend to choose this option when they need a better UI than Jenkins offers. However, the main advantage of self-hosting is that you have more control over the security of your own data.

- Implementing CI requires a cultural change, especially from management. They should allow time for these "unproductive things" to be done, but other routine tasks are put on hold as well.

- Nevertheless, a short time sacrifice translates into a long-term benefit for the company as a whole. With Jenkins, your code is easier to maintain and fewer bugs. Teams are more integrated and deployment times are reduced. Your business can deploy faster and respond to the changing needs of your customers.

##### All of this requires a mindset shift

- CI is an investment, not a cost. The ROI for implementation can be produced with high-quality products that are time-saving, error-proof, and more readily available to customers.

## Jenkins automation

Today Jenkins is a leading open source automation server with around 1,400 plugins to support all kinds of development tasks. The continuous integration and continuous delivery of Java code that Kawaguchi was originally trying to address: building projects, running tests, running static code analysis, and deploying are just one of the many processes people are using Jenkins to automate. These 1,400 plugins cover five areas (platform, UI, management, source code management, and the most used build management).

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)

## How Jenkins Works

Jenkins is available in the form of Java 8 WAR archives and installation packages, Homebrew packages, Docker images, and source code for major operating systems. The source code is mostly Java, and contains several Groovy, Ruby, and Another Tool For Language Recognition (ANTLR) files.<br>

You can run the Jenkins WAR alone or as a Serverlet on a Java application server such as Tomcat. In either case, it creates a web user interface (UI) and accepts calls to REST APIs.


### Jenkins plugin

Once installed, Jenkins allows the user to accept a default list of plugins or select the plugins they want. The Jenkins main screen displays the current Build Queue and Executor status, creating a new item (Job), managing users, viewing build history, managing Jenkins, viewing customized views of users, and certificates of users. <br>
Provides a link to manage New Jenkins items can be any of the six types of tasks + folders for item management. The Manage Jenkins page allows you to do 18 things, including the option to open a command line interface.

### Jenkins pipeline

Once you've configured Jenkins, it's time to create some projects that Jenkins can build. You can also use the web UI to write the script, but the best study right now is to create a pipeline script named Jenkinsfile and check it into the repository. <br>

In the default Jenkins installation, the branch source for this kind of pipeline can be Git or Subversion, including GitHub. If you need a different kind of repository or another online repository, just add the appropriate plugin and reboot Jenkins. <br>

Jenkins pipelines can be declarative or scripted. The simpler of the two, the declarative pipeline uses a Groovy-compatible syntax, and if desired, you can start the file with #!groovy to direct the code editor in the right direction. A declarative pipeline starts with a pipeline block, defines an agent, and defines stages that contain executable steps, as in the following three-stage example. <br>

```
pipeline {
agent any

stages {
stage(‘Build’) {
steps {
echo ‘Building..’
}
}
stage(‘Test’) {
steps {
echo ‘Testing..’
}
}
stage(‘Deploy’) {
steps {
echo ‘Deploying....’
}
}
}
}
```

pipeline is an essential outer block for calling Jenkins pipeline plugins. The agent defines where you want to run the pipeline. any indicates that any available agent can be used to run the pipeline or stage. For example, if you are a more specific agent, you would declare a container to use as follows.

```
agent {
docker {
image ‘maven:3-alpine’
label ‘my-defined-label’
args ‘-v /tmp:/tmp’
}
}
```

stages contain one or more stage directives. In the previous example, the three stages are Build, Test, and Deploy.
steps do the actual work. In the previous example, steps only displayed a message. A more useful build step would be:

```
pipeline {
agent any

stages {
stage(‘Build’) {
steps {
sh ‘make’
archiveArtifacts artifacts: ‘**/target/*.jar’, fingerprint: true
}
}
}
}

```

In this example, we are archiving the generated JAR file to the Jenkins archive after calling make from the shell.
The post session defines an action to be executed at the end of the stage or pipeline execution. Multiple post-condition blocks can be used within a post session (always, changed, failure, success, unstable, and aborted).
For example, the following Jenkins always runs Junit after the Test stage, but only sends an email if the pipeline fails.

```
pipeline {
agent any
stages {
stage(‘Test’) {
steps {
sh ‘make check’
}
}
}
post {
always {
junit ‘**/target/*.xml’
}
failure {
mail to: team@example.com, subject: ‘The Pipeline failed :(‘
}
}
}
```

Directive pipelines can express most of what the user needs to define a pipeline, and are much easier to learn than the scripted pipeline syntax, which is a Groovy-based DSL. In fact, a scripted pipeline is a programming environment with all its characteristics.


> Declarative pipeline

```
pipeline {
agent { docker ‘node:6.3’ }
stages {
stage(‘build’) {
steps {
sh ‘npm ?version’
}
}
}
}
```

> Scripted pipeline

```
node(‘docker’) {
checkout scm
stage(‘Build’) {
docker.image(‘node:6.3’).inside {
sh ‘npm ?version’
}
}
}
```

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#DevOps)