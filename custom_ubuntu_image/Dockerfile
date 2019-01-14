FROM ubuntu
RUN apt-get update
RUN apt-get install -y apache2
RUN apt-get install -y apache2-utils
COPY index.html /var/www/html/index.html
CMD echo "ServerName localhost" >> /etc/apache2/apache2.conf
ENTRYPOINT ["apache2ctl"]
CMD ["-D","FOREGROUND"]
EXPOSE 80

#FROM Alpine
#COPY script.sh /script.sh
#CMD ["/script.sh"] 

[CMD VS ENTRYPOINT]

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
