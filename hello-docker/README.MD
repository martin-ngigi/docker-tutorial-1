##Docker tutorial.

YouTube Link ->  https://www.youtube.com/watch?v=pTFZFxd4hOI&t=1206s
Docker Hub -> https://hub.docker.com/
Play with docker -> https://labs.play-with-docker.com/

#Docker
Is a latform for building, running and shipping applications. i.e. if your application runs in developing machine, it will also run in another machine.

#Reasons why app may fail to run in another machine:
	-One or more missing files.
	-Software version mismatch.
	-Different configuration settings.
	
With docker, allows to an app in different software versions side by side. i.e one version is v7 and other is v8.

Docker remove app command:
	docker-compose down rmi --all
	
#Container Vs Virtual machines:
1. Container is an isolated environment for running an application while Virtual machine is an abstraction of machine(physical hardware).

#Problems of running application in a virtual machine:
1. Each VM requires a full-blown Os.
2. Slow to start.
3. Resource intensive i.e. cpu, RAM.

#Adavntages of running application in a container:
1. Allow runnig multiple applications in isolation.
2. Lightweight - dont need a full OS.
3. Use the OS of the host.
4. Start quickly - fast.
5. Need less hardware resorce - i.e. ram, cpu, disk.

	CMD node app.js 

#Docker architecture.
- Uses a client server(Docker Engine.) architecture.
- Client communicates to the server through server API.

#Dockerizing application,
- Making small change so that the app can be run by docker by running a docker file.
- Docker fle - a plain text file that docker uses to package the app into an image.
- The image contains everything the application needs to run such as:
	1. A cut-down OS
	2. A runtime environment such as Node, Python.
	3. Application files.
	4. Third party library.
	5. Environment variables.
-Once we have the image, we tell docker to start the container using that image.

From development, we push the image to Registry (DockerHub - ie similar to github for storage), in Test/Production environment we can run the app stored in Registry.

#Check version
Run: 
	docker version

#Deploying an application
Paste the following commands in the Dockerfile
Import node:alpine  distribution of linux image:
	FROM node:alpine
Copy evrything from current directory i.e. "." to "app" directory:
	COPY . /app
Specify the work directory:
	WORKDIR /app
Run a command to start the app.js file we have created:
	CMD node app.js 

#Packaging the application
Run following commands in terminal.
buld: "-t" is the tag, "hello-docker" is the file to be created,"." is the current directory. :
	docker build -t hello-docker .
#Docker image
To view all images run:
	docker image ls
or:
	docker images

To run the image, regardless of the directory on is, run :
	docker run hello-docker
	
#Create repository in docker hub
url -> https://hub.docker.com/repositories/martinngigi
Create docker image docker hub similar to the one present locally

	docker tag local-image:tagname new-repo:tagname
	docker push new-repo:tagname

i.e.
docker tag hello-docker:latest hello-docker:latest
docker push hello-docker:latest

i.e. 2 (Working)
	docker login -u martinngigi
	docker tag hello-docker:latest martinngigi/hello-docker:myfirstimagepush
	docker push martinngigi/hello-docker:myfirstimagepush

#Pulling docker image and it in play-with-docker:
url -> https://labs.play-with-docker.com/
	docker login
	docker pull martinngigi/hello-docker:myfirstimagepush
	
run docker while in play-with-docker
	docker run martinngigi/hello-docker:myfirstimagepush
	
#LINUX COMMANDS(Ubuntu)
cd C:\Users\Administrator\Desktop\Docker\docker-tutorial-1\hello-docker>
Running ubuntu:
	docker run ubuntu
View running containers:
	docker ps
View all running containers:
	docker ps -a
Start and run a container and interact with it. The result is "root@bfccb2f89288:/#" 
... This is a shell. A shell is a program that takes our commands and passes them to the OS for execution.
"root" the current logged in user. "bfccb2f89288" is the name of the machine. "/" is the root directory. "#" Means we have the highest privileges.
"it"  stands for interactive:
	docker run -it ubuntu
	
while in "root@bfccb2f89288:/#" 
run following commands:
	echo Hello world
	whoami						-> This will who show current logged in user
	echo $0 					-> This will show current dir of the program
	history						-> This will show previously typed commands
	
	

	
	