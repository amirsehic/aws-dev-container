# aws-dev-container
Development container based on Amazon Linux

## Motivation
I wanted to automate building and rebuilding (with adjustments) my development environment, while minimizing the amount of software packages installed on my host OS (macOS). And since I primarily work on AWS native applications, I wanted my development container to be based on Amazon Linux.

## Prerequisites
1. Docker - https://www.docker.com/
1. (optional) A text editor like Visual Studio Code - https://code.visualstudio.com/
1. (optional) Modify the Dockerfile to install software packages you use in your development environment.

## Usage
Initially I used the following shell commands to  
build the image (Note that you can first edit the AWS conguration in .aws folder, as well as .bashrc file.)
```
docker build --no-cache -t local/dev-image .
```
build and start the container (Note that you need to replace \<folder that contains your project folders\> with the path on your host system that you want to mount to /workspaces/projects in the container.)
```
docker run -it -v <folder that contains your project folders>:/workspaces/projects --name dev local/dev-image
```
and restart the contaner
```
docker start -ia dev
```

Now I use **Visual Studio Code Remote - Containers** extension to develop inside this container - https://code.visualstudio.com/docs/remote/containers.

The .devcontainer/devcontainer.json file that works with this Dockerfile is included. The .devcontainer and dev-image folders need to be in the \<folder that contains your project folders\> (the one mounted into the /workspaces folder in the container). I am trying to figure out how to remove this limitation.