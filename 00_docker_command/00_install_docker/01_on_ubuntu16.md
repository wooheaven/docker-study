# Uninstall old versions
```
sudo apt-get remove docker docker-engine docker.io
```

# update apt
```
sudo apt-get update
```

# Install packages to allow apt to use a repository over HTTPS:
```
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

# Add Docker’s official GPG key and Verify
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
```

# add stable repository
```
ubuntu@ubuntu:~$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

# Install Docker-CE
```
sudo apt-get update
sudo apt-get install docker-ce
```

# Verify docker-ce
```
docker --version
docker run hello-world
```

# Uninstall Docker-ce
```
sudo apt-get purge docker-ce
sudo rm -rf /var/lib/docker
```

# real log
```
ubuntu@ubuntu:~$ sudo apt-get remove docker docker-engine docker.io
[sudo] password for ubuntu:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'docker-engine' is not installed, so not removed
Package 'docker' is not installed, so not removed
Package 'docker.io' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 101 not upgraded.

ubuntu@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://kr.archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://kr.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:4 http://kr.archive.ubuntu.com/ubuntu xenial-backports InRelease
Fetched 102 kB in 13s (7,723 B/s)
Reading package lists... Done

ubuntu@ubuntu:~$ sudo apt-get install \
>     apt-transport-https \
>     ca-certificates \
>     curl \
>     software-properties-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
apt-transport-https is already the newest version (1.2.24).
software-properties-common is already the newest version (0.96.20.7).
The following additional packages will be installed:
  libcurl3-gnutls
The following packages will be upgraded:
  ca-certificates curl libcurl3-gnutls
3 upgraded, 0 newly installed, 0 to remove and 98 not upgraded.
Need to get 490 kB of archives.
After this operation, 58.4 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://kr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ca-certificates all 20170717~16.04.1 [168 kB]
Get:2 http://kr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 curl amd64 7.47.0-1ubuntu2.5 [138 kB]
Get:3 http://kr.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcurl3-gnutls amd64 7.47.0-1ubuntu2.5 [184 kB]
Fetched 490 kB in 15s (31.4 kB/s)
Preconfiguring packages ...
(Reading database ... 59734 files and directories currently installed.)
Preparing to unpack .../ca-certificates_20170717~16.04.1_all.deb ...
Unpacking ca-certificates (20170717~16.04.1) over (20160104ubuntu1) ...
Preparing to unpack .../curl_7.47.0-1ubuntu2.5_amd64.deb ...
Unpacking curl (7.47.0-1ubuntu2.5) over (7.47.0-1ubuntu2.2) ...
Preparing to unpack .../libcurl3-gnutls_7.47.0-1ubuntu2.5_amd64.deb ...
Unpacking libcurl3-gnutls:amd64 (7.47.0-1ubuntu2.5) over (7.47.0-1ubuntu2.2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Setting up ca-certificates (20170717~16.04.1) ...
Setting up libcurl3-gnutls:amd64 (7.47.0-1ubuntu2.5) ...
Setting up curl (7.47.0-1ubuntu2.5) ...
Processing triggers for ca-certificates (20170717~16.04.1) ...
Updating certificates in /etc/ssl/certs...
17 added, 42 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
Processing triggers for libc-bin (2.23-0ubuntu9) ...

ubuntu@ubuntu:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
OK

ubuntu@ubuntu:~$ sudo apt-key fingerprint 0EBFCD88
pub   4096R/0EBFCD88 2017-02-22
      Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid                  Docker Release (CE deb) <docker@docker.com>
sub   4096R/F273FCD8 2017-02-22

ubuntu@ubuntu:~$ sudo add-apt-repository \
>    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
>    $(lsb_release -cs) \
>    stable"

ubuntu@ubuntu:~$ sudo apt-get update
Get:1 https://download.docker.com/linux/ubuntu xenial InRelease [65.8 kB]
Get:2 https://download.docker.com/linux/ubuntu xenial/stable amd64 Packages [3,150 B]
Hit:3 http://kr.archive.ubuntu.com/ubuntu xenial InRelease
Hit:4 http://kr.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:5 http://kr.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:6 http://security.ubuntu.com/ubuntu xenial-security InRelease
Fetched 69.0 kB in 10s (6,481 B/s)
Reading package lists... Done

ubuntu@ubuntu:~$ sudo apt-get install docker-ce
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  aufs-tools cgroupfs-mount libltdl7
Suggested packages:
  mountall
The following NEW packages will be installed:
  aufs-tools cgroupfs-mount docker-ce libltdl7
0 upgraded, 4 newly installed, 0 to remove and 98 not upgraded.
Need to get 30.3 MB of archives.
After this operation, 149 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 https://download.docker.com/linux/ubuntu xenial/stable amd64 docker-ce amd64 17.12.0~ce-0~ubuntu [30.2 MB]
Get:2 http://kr.archive.ubuntu.com/ubuntu xenial/universe amd64 aufs-tools amd64 1:3.2+20130722-1.1ubuntu1 [92.9 kB]
Get:3 http://kr.archive.ubuntu.com/ubuntu xenial/universe amd64 cgroupfs-mount all 1.2 [4,970 B]
Get:4 http://kr.archive.ubuntu.com/ubuntu xenial/main amd64 libltdl7 amd64 2.4.6-0.1 [38.3 kB]
Fetched 30.3 MB in 13s (2,267 kB/s)
Selecting previously unselected package aufs-tools.
(Reading database ... 59708 files and directories currently installed.)
Preparing to unpack .../aufs-tools_1%3a3.2+20130722-1.1ubuntu1_amd64.deb ...
Unpacking aufs-tools (1:3.2+20130722-1.1ubuntu1) ...
Selecting previously unselected package cgroupfs-mount.
Preparing to unpack .../cgroupfs-mount_1.2_all.deb ...
Unpacking cgroupfs-mount (1.2) ...
Selecting previously unselected package libltdl7:amd64.
Preparing to unpack .../libltdl7_2.4.6-0.1_amd64.deb ...
Unpacking libltdl7:amd64 (2.4.6-0.1) ...
Selecting previously unselected package docker-ce.
Preparing to unpack .../docker-ce_17.12.0~ce-0~ubuntu_amd64.deb ...
Unpacking docker-ce (17.12.0~ce-0~ubuntu) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (229-4ubuntu19) ...
Setting up aufs-tools (1:3.2+20130722-1.1ubuntu1) ...
Setting up cgroupfs-mount (1.2) ...
Setting up libltdl7:amd64 (2.4.6-0.1) ...
Setting up docker-ce (17.12.0~ce-0~ubuntu) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu19) ...
Processing triggers for ureadahead (0.100.0-19) ...

ubuntu@ubuntu:~$ docker --version
Docker version 17.12.0-ce, build c97c6d6

ubuntu@ubuntu:~$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
ca4f61b1923c: Pull complete
Digest: sha256:66ef312bbac49c39a89aa9bcc3cb4f3c9e7de3788c944158df3ee0176d32b751
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/
```
