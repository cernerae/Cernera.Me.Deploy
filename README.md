# WordPress-Docker

**Date: 12/27/2019**  
**Author: Edward Cernera**

<img src="https://stephenafamo.com/blog/wp-content/uploads/2017/03/docker-wordpress.png" data-canonical-src="https://stephenafamo.com/blog/wp-content/uploads/2017/03/docker-wordpress.png" width="400" height="200" />

# Purpose
Deploy a WordPress website with docker-compose, NGINX and MySQL on CentOS

# Virtual Machine Setup
## Update yum & Install Basic Packages
`sudo yum update -y`  
`sudo yum install git wget vim -y`

## Add Additional Users
`sudo useradd alenza`  
`sudo usermod -aG wheel alenza`
`sudo passwd alenza`

(Optional) Switch to user "alenza": `su alenza`

## Install Docker
### Update Kernel

Clone the Docker-Scripts repository:
`cd ~`  
`git clone https://github.com/cernerae/DockerInstall.git`

`cd Docker-Scripts/dev/util`

Update the kernel. This script will reboot virtual machine on completion:  
`sudo bash update_kernel_preboot`

SSH back into the virtual machine:  
`sudo bash update_kernel_postboot`

### Install Docker

To install Docker:  
`sudo bash install_docker`

This script will also install docker-compose.

Add your non-root users to the docker group:  
`sudo usermod -aG docker cernera`

Exit the shell:
`exit`

# Install WordPress with docker-compose

Clone this repository:  
`cd ~`  
`git clone https://github.com/cernerae/DockerWordpress.git`  
`cd docker`

Run:  
`docker-compose up -d`

To bring it down (keep database):  
`docker-compose down`

To bring it down (remove database):  
`docker-compose down --volumes`
