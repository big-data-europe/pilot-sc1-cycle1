# Pilot cycle 1 for SC 'Health': _integrating the Open PHACTS functionality on the BDE platform_

### _IMPORTANT: This repository is work in progress. We expect a stable release end of August 2016._
* [Overview](#overview)
* [Background Open PHACTS](#background)
* [Requirements](#requirements)
* [Linux installation](#linux-installation)
* [Windows installation](#windows-installation)

## Overview
This repository is meant to provide insight into the technical procedure and requirements of the first pilot for [Societal Challenge "Health"](https://www.big-data-europe.eu/health/) and to guide you to install it by yourself. By understanding the technology and the process-flows, we hope to encourage you to use it for your own domain. The goal of the pilot is to facilitate the [Open PHACTS Discovery Platform functionality](https://dev.openphacts.org/) via Docker containers on the Big-Data-Europe infrastructure. The Open PHACTS platform is built for researchers in Drug Discovery, however by design the technology itself is independent from the domain. Once you got familiar with the code and got it running by yourself, you should have enough experience to upload your own Linked Data, and create your own API.



## Background
The [Open PHACTS foundation](http://www.openphactsfoundation.org/) (BigDataEurope consortium partner) is dedicated to developing and sustaining the Open PHACTS Discovery Platform. The platform is the result of an [Innovative Medicines Initiative (IMI)](http://www.openphactsfoundation.org/about/project-history/) project and facilitates researchers to access and query publicly-available pharmacological data. 
[Stian Soiland-Reyes](https://github.com/stain) is the main contributor and leader of the [Open PHACTS docker](https://github.com/openphacts/ops-docker) work.
In collaboration with the [VU University Amsterdam](http://www.vu.nl) (both a member of the Open PHACTS foundation and the BigDataEurope consortium), the Open PHACTS foundation leads the work on Societal Challenge "Health" (SC1) in the BigDataEurope project. 
All the data brought together by Open PHACTS is free to access, to help researchers in drug discovery to find and use the information they need.in the BigDataEurope consortium. 


## Requirements

Roughly minimal hardware requirements:
  - ~ 150 GB of disk space
  - ~ 10 GB of RAM
  - ~ 4 CPU core

Recommended hardware:
  - ~ 250 GB of SSD disk
  - ~ 128 GB of RAM
  - ~ 8 CPU cores

Prerequisites:

  - Windows 7,8 or 10 **or** a recent x64 Linux distribution (e.g. Ubuntu 14.04 LTS, Centos 7) 
  - [Docker](https://docs.docker.com/installation/#installation) 1.7.1 or later
  - [Docker Compose](http://docs.docker.com/compose/install/) 1.5.2 or later
  - Fast Internet connection (during build of data containers)

Note that the you would have to make the
[disk space available for Docker](#disk-space-for-docker).

## Linux installation
Available for recent x64 Linux install (e.g. 
At this moment the installation is only using _docker-compose_ and _docker-machine_. The BigDataEurope Docker infrastructure also uses _docker-swarm_ and its own conventions,  templates, namespace allocation etc. The migration process is in progress.

For instructions please visit: [Open PHACTS Docker images](https://github.com/openphacts/ops-docker)

## Windows installation
Successfully tested on a Windows 10 Home (version 1511) machine with Intel Core i7-6920HQ CPU @ 2.90GHz, 32 GB RAM, 256 GB SSD and [Docker Toolbox v1.11.2](https://github.com/docker/toolbox/releases/download/v1.11.2/DockerToolbox-1.11.2.exe)

### Step 1: Removing previous installation of Docker Toolbox

If this is the first time you install Docker Toolbox on your machine, things should be fine and you can skip to the next step. But if not, this tutorial only works if you removed the previous install. The reason is that the Toolbox comes with the Oracle VirtualBox, which is quite buggy in Windows 10. For example, when you close the VirtualBox GUI, it might still run in the background which causes GUI problems and even more important, messing up config files. 
If you have important work which would be lost by the reinstall, please make a backup, or do not continue this manual.
The easiest way to uninstall the Toolbox stuff is simply removing the `.docker` and `.VirualBox` folders from your home directory. It might be that Windows does not allow you to remove the folders because an active docker-machine/VirtualBox instance blocks the delete option. In that case check if the service is not on auto-start and reboot the machine.

### Step 2: Installing Docker Toolbox


  - [Download and install Docker Toolbox](https://www.docker.com/products/docker-toolbox)
  - After install, **never** open _Oracle Virtualbox_, because it can mess up the config for some reason. 
  - Also **never** open _Docker Quickstart_, because it automatically generates a default machine that does not have the right settings to run this pilot. 

### Step 3: Creating a docker-machine
  - Open a Command prompt (click on magnifying glass left bottom and type 'cmd')
  - Create a docker-machine with a 150GB virtual disk (this is the minimum): `docker-machine create --virtualbox-disk-size 150000 -d virtualbox default`
  Expected output similar to:
```
Creating CA: /home/username/.docker/machine/certs/ca.pem
Creating client certificate: /home/username/.docker/machine/certs/cert.pem
Image cache does not exist, creating it at /home/username/.docker/machine/cache...
No default boot2docker iso found locally, downloading the latest release...
Downloading https://github.com/boot2docker/boot2docker/releases/download/v1.6.2/boot2docker.iso to /home/username/.docker/machine/cache/boot2docker.iso...
Creating VirtualBox VM...
Creating SSH key...
Starting VirtualBox VM...
Starting VM...
To see how to connect Docker to this machine, run: docker-machine env default
```
