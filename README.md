# DevEnv-Docker-LEMP-Drupal

Development Environment using Docker implementing a LEMP server used for hosting Drupal applications.

[LEMP] = Ubuntu 20.04 Base Image + Nginx + MySQL + PHP 7.4 


## Quick Start Guide

To get this docker container up and running simply build and start using the following commands from within the `docker` directory.

`> cd docker`

`> ./build.sh`

`> ./start.sh`

You can access the application at `https://127.0.0.1/drupalwebapp/`

Once finished call the stop command to bring down docker container and application.

`> ./stop.sh`

While the docker container is running, ie after running `./start` you can connect to the server to run commands as if you would any other server. Use the following command to connect

`> ./connect.sh`


The following section provides further details on the docker methods used within each script.


## Build

You only need to build the application once.
Once built, you can simply run the application each time you need this development environment. 

1. Build the base image.

`> cd docker/lemp-base`

`> docker build . -t lemp-dev-base`

Check image with name 'lemp-dev-base' has been created

`> docker images`


2. Build the application image (which will utilise the base image created in step 1).

Move into directory 'docker/lemp-dev'.

`> cd ..`

`> cd lemp-dev`

Build the application image

`> docker build . -t lemp-dev`

Again, to check this image was created run the command and look for 'lemp-dev' has been created

`> docker images`


## Run

Navigate to directory '/docker'
and start the docker container using

`> docker-compose up -d`

This will start a docker container named 'drupalwebapp'.
serving up the contents of folder '/www/'.

To connect directly to this container (LEMP server)

`> docker exec -it drupalwebapp /bin/bash`

To stop the docker container use

`> docker-compose down`


## Access 

View web page at the following url 

https://localhost/index.html

https://127.0.0.1/index.html

Served from folder '/www/index.html'

or

https://localhost/drupalwebapp/

https://127.0.0.1/drupalwebapp/

Served from Drupal application '/www/drupalwebapp/public'


#### MySQL

Use the credentials in the command below to access mysql in your docker container.

- Host: 0.0.0.0
- User: drupal_user
- Password: password


`> mysql -h 0.0.0.0 -u drupal_user -p`


___

This project is based on 
<a href="https://github.com/aalshukri/DevEnv-Docker-LEMP-Laravel">https://github.com/aalshukri/DevEnv-Docker-LEMP-Laravel</a>