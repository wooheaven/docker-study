# ref
```
https://docs.docker.com/engine/installation/linux/ubuntu/#prerequisites
```

# OS requirements
```
cat /etc/issue
Ubuntu 14.04.5 LTS \n \l

uname -a
Linux rwoo-A610 4.4.0-31-generic #50~14.04.1-Ubuntu SMP Wed Jul 13 01:07:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

# Uninstall old versions
```
docker --version
Docker version 1.12.1, build 23cf638

sudo apt-get remove docker docker-engine docker.io
sudo dpkg -l | grep docker
rc  docker-engine                                         1.13.0-0~ubuntu-trusty                              amd64        Docker: the open-source application container engine
sudo dpkg --purge docker-engine
sudo apt-get autoremove
sudo apt-get autoclean
sudo dpkg -l | grep docker
```

# The contents of /var/lib/docker/, including images, containers, volumes, and networks, are preserved.
```
sudo rm -rf /var/lib/docker
```

# Recommended extra packages for Trusty 14.04
```
sudo apt-get update
sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual
```

# Install packages to allow apt to use a repository over HTTPS:
```
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

# Add Docker’s official GPG key:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
OK
    
sudo apt-key fingerprint 0EBFCD88
/etc/apt/trusted.gpg
--------------------
...
pub   4096R/0EBFCD88 2017-02-22
Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid                  Docker Release (CE deb) <docker@docker.com>
sub   4096R/F273FCD8 2017-02-22
```

# Use the following command to set up the stable repository.
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
or
sudo vi /etc/apt/sources.list.d/docker.list # amd64 is x64 server

cat /etc/apt/sources.list.d/docker.list
deb [arch=amd64] https://download.docker.com/linux/ubuntu trusty stable
```

# Update the apt package index.
```
sudo apt-get update
```

# Install the latest version of Docker.
```
sudo apt-get install docker-ce
```

# Add docker group after install docker 
```
sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot
```

# Verify that docker-ce is installed correctly by running the hello-world image.
```
docker --version
Docker version 17.03.0-ce, build 3a232c8

docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
78445dd45222: Pull complete 
Digest: sha256:c5515758d4c5e1e838e9cd307f6c6a0d620b5e07e6f927b07d05f6d12a1ac8d7
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
        to your terminal.

To try something more ambitious, you can run an Ubuntu container with:

docker run -it ubuntu bash

 Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

 For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/

docker images 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hello-world         latest              48b5124b2768        2 months ago        1.84 kB
```
