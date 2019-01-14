# Docker-hands-on

To start with docker 

docker image pull alpine
Pull the alpinr image from Docker registry

docker image ls
To check how many images you have locally setup

docker container run alpine ls -l
To run docker container with alpine image

docker container run alpine echo "hello from alpine"
It will start the alpine container, execute the command and the container will be killed

Every time, a new container will be created

docker container run -it alpine /bin/sh
To run the container in interactive mode

exit
This will close the container and exit

docker container ls
It will show the status of the running container

docker container ls -a
It will show all the containers, which have started and closed.

docker container start <container_id>
To start a container, which is stopped

docker image inspect alpine
To find out more about a Docker image, run 

docker container run -it ubuntu bash
Bash terminal will be opened on the container

docker container diff <container ID>
To inspect all the changes, you have made in the container

To create an image and keep the changes in it for later use.
docker container commit CONTAINER_ID

docker image tag <IMAGE_ID> ourfiglet(name of the image)
Once you have, commited the image, you have to give the name to 


docker image inspect alpine
To inspect about the images details

docker build -t webserver .
dot means this docker file

docker images

docker container run -dit (container will not open, it will be in the foreground)

docker inspect NAMES | grep IP

docker ps -a  (It will give only running container)

docker rm $(docker ps -aq)  (It will remove all containers)

docker stop $(docker ps -aq) (It will stop all running containers)

docker kill $(docker ps -aq)

docker run -dit --name=abc -p 80:80/tcp webserver:v2
iptables -t nat -nvL
netstat -luntp
docker run -dit --net=host webserver:v2 

[ CMD VS ENTRYPOINT ]

() CMD is by-default instruction which is executed when we run a container
FROM ubuntu
CMD echo "Echo hello sameed" 
docker run -it container and the echo command will be executed

docker run -it container echo "hello from  the other side"  (It will overide the echo which is define in the docker file) 

FROM ubuntu
CMD echo "Echo hello sameed"
CMD echo "Echo hello sada" 
Now, only the sada echo will be executed

[ ENTRYPOINT ]
It is also a runtime instruction as CMD 

FROM ubuntu
ENTRYPOINT ["echo","Hi Docker"]

When we run this container with parameter, it will append the commands in.
(Hi Docker echo Hi sameed )

From ubuntu
ENTRYPOINT ["echo"]
CMD ["Hi Docker"] #it will be argument for entrypoint instruction
#Now, the dynamic arguments will be perform smoothly.


{---- Push repository to docker hub -----}

So, this means you have to tag your image before pushing:
[docker tag firstimage YOUR_DOCKERHUB_NAME/firstimage"]
and then you should be able to push it.
[docker push YOUR_DOCKERHUB_NAME/firstimage"]

docker push image_name
