Check version: 
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


