FROM ubuntu
RUN apt-get update
RUN apt-get install -y apache2
RUN apt-get install -y apache2-utils
COPY index.html /var/www/html/index.html
CMD echo "ServerName localhost" >> /etc/apache2/apache2.conf
ENTRYPOINT ["apache2ctl"]
CMD ["-D","FOREGROUND"]
EXPOSE 80


