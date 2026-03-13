#FREEContainer
FROM ubuntu:latest
RUN apt update -y && apt install nginx -y
COPY index.html /var/www/html/index.nginx-debian.html
EXPOSE 80
ENTRYPOINT [ "nginx" ] 
CMD [ "-g" , "daemon off;" ]