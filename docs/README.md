# Running XNAT on Docker for Windows
This tutorial shows how to deploy an XNAT instance on Docker for Windows.

## Introduction
This tutorial is based on the official [Dockerized XNAT](https://github.com/NrgXnat/xnat-docker-compose) repository. It addresses the common pitfalls encountered when deploying the XNAT containers on Windows.

## Prerequisites
* Install [Git for Windows](https://git-scm.com/downloads)
* Install Docker
    * Use [Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/) if your Windows system includes Hyper-V support. Make sure that you have [enabled Hyper-V](https://docs.docker.com/machine/drivers/hyper-v/) before installing Docker
    * Use [Docker Toolbox on Windows](https://docs.docker.com/toolbox/toolbox_install_windows/) if your Windows system does not include Hyper-V
    
## Download Dockerized XNAT
You can either download the [Dockerized XNAT](https://github.com/NrgXnat/xnat-docker-compose) repository directly from GitHub, or clone it using Git Bash:
```plaintext
git clone https://github.com/NrgXnat/xnat-docker-compose
```
If you chose to clone the repository then make sure to have set git core.autocrlf configuration to input before running the clone command:
```plaintext
git config --global core.autocrlf input
```
This will avoid running into line-ending issues during the deployment process.

## Building and running with Docker Compose
Follow the steps outlined in the [Dockerized XNAT](https://github.com/NrgXnat/xnat-docker-compose) repository usage section.
* Open a terminal window (Git Bash, Docker Quickstart Terminal, or PowerShell, *but not* PowerShell ISE), and change the directory to where you have downloaded/cloned xnat-docker-compose
* Start the system
```plaintext
    $ docker-compose up -d
```
* The building process takes few minutes. To follow progress use
```plaintext
    $ docker-compose logs -f --tail=20 xnat-web
```
* Once the XNAT server is started it will be available at the Docker machine IP address
```plaintext
    $ docker-machine ip
```

## Stopping & staring the system
To stop the XNAT server without removing the containers:
```plaintext
$ docker-compose stop
```
The system can be started again with
```plaintext
$ docker-compose start
```

## Stopping & removing the system
To stop the system and remove containers and volumes (*removes all data*):
```plaintext
$ docker-compose down
```
