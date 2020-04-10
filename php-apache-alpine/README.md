# Dockerize
A docker image that installs PHP 7 on apache 2.4 and Alpine linux 3.11.
Written based on the official PHP docker image (https://hub.docker.com/_/php)
### PHP,NODEJS (APACHE) on ALPINE 3.11
Alpine            |  Apache     |  PHP
:-------------------------:|:-------------------------:|:-------------------------:
![](https://www.alpinelinux.org/alpinelinux-logo.svg)  |  ![](https://blog.pierrevieville.fr/wp-content/uploads/2019/02/apache2-virtualhosts.jpg) |  ![](https://www.emaginance.com/wp-content/uploads/2015/12/php7.jpg)

### Installation
- Make sure docker installed on your machine
- Clone the folder and change directory to `php-apache-alpine/`
- Build the image using:
  - `docker build . -t "php-alpine-apache"`
- Make sure the image is built by listing images and finding image with the name "php-alpine-apache":
  - `docker images -a`
- Run this docker image in background using:
  - `docker run -p 8080:80 -d php-alpine-apache`
- Make sure the container is there by listing all containers and find the last one with the service "/opt/entrypoint.sh":
  - `docker ps -a` get [NAME_OF_CONTAINER_RUNNING].
- Go to localhost:8080 and check apache is working fine:
![](https://i.ibb.co/VLDW8cV/Screen-Shot-2020-03-22-at-3-15-10-PM.png)
- To check if php is working fine:
  - SSH to the container specifying the bash command to allow bash scripting : 
    - `docker exec -it NAME_OF_CONTAINER_RUNNING /bin/bash`
  - change directory to the root folder of the web 
    - `cd /var/www/html/`
  - create index.php file 
    - `nano index.php`
  - add the following instrutions to allow displaying php configuration info 
    - `<?php echo phpinfo();?>`
  - go back to localhost:8080, you will get php info:
![](https://i.ibb.co/1T7Gzcg/Screen-Shot-2020-03-22-at-3-33-34-PM.png)
