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

{--- Create a new network ---}

When we have to ping the container with it's name, we have to create a new network.
For reference:
https://www.youtube.com/watch?v=Tx12haz-4VA&index=5&list=PLH1ul2iNXl7uhEOpPBYyUVktV7nW_15sh

{--- Docker Swarm ---}

docker swarm init (TO initialize a machine)
[docker swarm init --advertise-addr 159.89.197.250]

We make service on our manager, in which our app is installed

docker swarm join --token SWMTKN-1-03gx4eq7ea6gajku2klr9smtynnn1pji43jc0zh5xzkrgb2miv-9no536cwq57bxgwbwircw4pbv 159.89.197.250:2377

Master machine is initialized. To check,write
docker info

To check the status of cluster
docker node ls

To join node with master node, run the jooin command as stated above

Once the worker node is added, Now you can run any command from Master node

Now create docker service

####################################    Edureka   #####################################################
#################################### Docker swarm ##################################################### 

docker swarm init --advertise-addr <ip-addr>      [[ Initialize the swarm]]
docker service ls 								  [[ list services ]]
docker service ps <name> 						  [[list task of services]]
docker service create <name> <image-name> 	      [[ create new service ]]
docker service rm <name> 						  [[ remove service ]]
docker service scale <name>=5					  [[ scale services ]]
docker swarm leave --force 						  [[ Leave the swarm ]]
dokcer info | grep Swarm
docker swarm join-token manager
docker service task <id>
service docker start

docker node ls 									  [[ List the nodes ]]
docker node ps 									  [[ list service in nodes ]]
remove node 									  [[docker node rm <id>]]

{{ docker swarm cluster management }}
docker node update --availability drain <node>    [[ It will stop the node for scheduling ]]
docker node update --availability active <node>    [[ It will start the node for scheduling ]]
docker node promote <node> 						  [[ Promotes the node as manager ]]
docker node demote <node> 						  [[ Demotes the node from manager role ]]
docker node rm <node> 							  [[ Removes the node from cluster ]]

############################### Practical work ##########################################################

Manager: docker swarm infoit --advertise-addr 159.89.197.250
	     docker node ls
	     docker service create --name "Ang-App" -p 4200:4200 demoapp1
	     docker service create --name frontend --replicas 5 -p 80:80/tcp bitnami/apache [Now five containers will be created on the manager & worker node]
	     docker service create --name redis redis:3.0.6
	     docker service ls
	     docker service task 

Worker: docker swarm join --token SWMTKN-1-0mgo2k12l2nel4th0p14a1tlwe8undxepss1631yysh5jqty79-1uwpl6j33otp14uyrfyj6w5au 159.89.197.250:2377
(1- Run the tocken on the workers end )


docker run -it -d -p 8080:8080 -v /var/run/docker.sock:/var/run/docker.sock dockersamples/visualizer
57e2b70ef235
57e2b70ef235:/#
