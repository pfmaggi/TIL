# Some useful docker commands

As usual, more a remainder for myself than anything new or ground-breaking.

# basic commands
## Some of the basics for images:
to list all the docker images available on the machine
    
    docker images

Download the latest version of an image from docker hub:

    docker pull imiell/chaos

Download a specific version of an image from docker hub:

    docker pull ubuntu:14.04

Run and image in the background:

    docker run -d imiell/chaos

Look at the layering information of an image:

    docker history <image name>

## Containers:
Once the image is running we can see the process and get the logs:

    docker top <container id>
    docker logs <container id>

To delete all the containers:

    docker rm -f $(docker ps -a -q)

To save the state of a running container:

    docker pause <container id>
    docker commit <container id> <image name>

To stop and restart a container:

    docker stop <container id>
    docker start <container id>

To know the status of a container we can use:

    docker inspect <container id>

this returns a json file with information about the container

To copy a file from the container to the host machine:

    docker cp <container id>:<path of the source file in the container> <destination path on the host machine>

To execute a command in the container we can use:

    docker exec <container id> <command to execute>

for example:

    docker exec cef38496c08db851bb6b1feca8354321f3b1ecead96dff3db9b58828c023962e touch /tmp/hello

To see the changes in the container:

    docker diff <container id>

    

## Docker containers with XWindows apps:

    docker run -d -p 5901:5901 -p 6080:6080 pfmaggi/myfirst2048image /bin/bash -c '/root/start_win2048.sh && sleep infinity'

## Pushing images to DockerHub
First you need to login into DockerHub:

    docker login

enter username and password, then you can push your image:

    docker push pfmaggi/myfirstwin2048

