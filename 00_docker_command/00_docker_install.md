# install docker CE on Ubuntu14.04 
```{text}
# ref

    https://docs.docker.com/engine/installation/linux/ubuntu/#prerequisites

# OS requirements

    rwoo@rwoo-A610:~$ cat /etc/issue
    Ubuntu 14.04.5 LTS \n \l

    rwoo@rwoo-A610:~$ uname -a
    Linux rwoo-A610 4.4.0-31-generic #50~14.04.1-Ubuntu SMP Wed Jul 13 01:07:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

# Uninstall old versions

    rwoo@rwoo-A610:~$ docker --version
    Docker version 1.12.1, build 23cf638

    rwoo@rwoo-A610:~$ sudo apt-get remove docker docker-engine 
    [sudo] password for rwoo: 
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Package 'docker' is not installed, so not removed
    The following packages were automatically installed and are no longer required:
      aufs-tools cgroup-lite
    Use 'apt-get autoremove' to remove them.
    The following packages will be REMOVED:
      docker-engine
    0 upgraded, 0 newly installed, 1 to remove and 1511 not upgraded.
    After this operation, 101 MB disk space will be freed.
    Do you want to continue? [Y/n] Y
    (Reading database ... 194645 files and directories currently installed.)
    Removing docker-engine (1.12.1-0~trusty) ...
    docker stop/waiting
    Processing triggers for man-db (2.6.7.1-1ubuntu1) ...

# The contents of /var/lib/docker/, including images, containers, volumes, and networks, are preserved.

    rwoo@rwoo-A610:~$ sudo rm -rf /var/lib/docker

# Recommended extra packages for Trusty 14.04

    rwoo@rwoo-A610:~$ sudo apt-get update
    rwoo@rwoo-A610:~$ sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual

# Install using the repository

# Set up the repository (Before you install Docker for the first time on a new host machine, you need to set up the Docker repository.)

# Docker CE

# Install packages to allow apt to use a repository over HTTPS:

    rwoo@rwoo-A610:~$ sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
    패키지 목록을 읽는 중입니다... 완료
    의존성 트리를 만드는 중입니다       
    상태 정보를 읽는 중입니다... 완료
    ca-certificates 패키지는 이미 최신 버전입니다.
    ca-certificates 패키지 수동설치로 지정합니다.
    software-properties-common 패키지는 이미 최신 버전입니다.
    software-properties-common 패키지 수동설치로 지정합니다.
    다음 패키지를 더 설치할 것입니다:
      libcurl3
    다음 패키지를 업그레이드할 것입니다:
      apt-transport-https curl libcurl3
    3개 업그레이드, 0개 새로 설치, 0개 제거 및 212개 업그레이드 안 함.
    321 k바이트 아카이브를 받아야 합니다.
    이 작업 후 2,048 바이트의 디스크 공간을 더 사용하게 됩니다.
    계속 하시겠습니까? [Y/n] Y
    받기:1 http://kr.archive.ubuntu.com/ubuntu/ trusty-updates/main curl amd64 7.35.0-1ubuntu2.10 [123 kB]
    받기:2 http://kr.archive.ubuntu.com/ubuntu/ trusty-updates/main libcurl3 amd64 7.35.0-1ubuntu2.10 [173 kB]
    받기:3 http://kr.archive.ubuntu.com/ubuntu/ trusty-updates/main apt-transport-https amd64 1.0.1ubuntu2.17 [25.0 kB]
    내려받기 321 k바이트, 소요시간 0초 (2,038 k바이트/초)
    (데이터베이스 읽는중 ...현재 172908개의 파일과 디렉터리가 설치되어 있습니다.)
    Preparing to unpack .../curl_7.35.0-1ubuntu2.10_amd64.deb ...
    Unpacking curl (7.35.0-1ubuntu2.10) over (7.35.0-1ubuntu2.7) ...
    Preparing to unpack .../libcurl3_7.35.0-1ubuntu2.10_amd64.deb ...
    Unpacking libcurl3:amd64 (7.35.0-1ubuntu2.10) over (7.35.0-1ubuntu2.7) ...
    Preparing to unpack .../apt-transport-https_1.0.1ubuntu2.17_amd64.deb ...
    Unpacking apt-transport-https (1.0.1ubuntu2.17) over (1.0.1ubuntu2.14) ...
    Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
    libcurl3:amd64 (7.35.0-1ubuntu2.10) 설정하는 중입니다 ...
    curl (7.35.0-1ubuntu2.10) 설정하는 중입니다 ...
    apt-transport-https (1.0.1ubuntu2.17) 설정하는 중입니다 ...
    Processing triggers for libc-bin (2.19-0ubuntu6.9) ...

# Add Docker’s official GPG key:

    rwoo@rwoo-A610:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    OK

    rwoo@rwoo-A610:~$ sudo apt-key fingerprint 0EBFCD88
    /etc/apt/trusted.gpg
    --------------------
    ...
    pub   4096R/0EBFCD88 2017-02-22
          Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
    uid                  Docker Release (CE deb) <docker@docker.com>
    sub   4096R/F273FCD8 2017-02-22

# Use the following command to set up the stable repository.

    rwoo@rwoo-A610:~$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Install Docker

# Update the apt package index.

    rwoo@rwoo-A610:~$ sudo apt-get update
    Ign http://kr.archive.ubuntu.com trusty InRelease
    Hit http://kr.archive.ubuntu.com trusty-updates InRelease                      
    Hit http://kr.archive.ubuntu.com trusty-backports InRelease                    
    Hit http://kr.archive.ubuntu.com trusty Release.gpg                            
    Hit http://kr.archive.ubuntu.com trusty-updates/main Sources                   
    Hit http://kr.archive.ubuntu.com trusty-updates/restricted Sources             
    Hit http://kr.archive.ubuntu.com trusty-updates/universe Sources               
    Hit http://kr.archive.ubuntu.com trusty-updates/multiverse Sources             
    Hit http://kr.archive.ubuntu.com trusty-updates/main amd64 Packages            
    Hit http://kr.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
    Hit http://kr.archive.ubuntu.com trusty-updates/universe amd64 Packages        
    Hit http://kr.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
    Hit http://kr.archive.ubuntu.com trusty-updates/main i386 Packages             
    Hit http://kr.archive.ubuntu.com trusty-updates/restricted i386 Packages       
    Hit http://kr.archive.ubuntu.com trusty-updates/universe i386 Packages         
    Hit http://kr.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
    Hit http://kr.archive.ubuntu.com trusty-updates/main Translation-en            
    Hit http://kr.archive.ubuntu.com trusty-updates/multiverse Translation-en      
    Hit http://kr.archive.ubuntu.com trusty-updates/restricted Translation-en      
    Hit http://kr.archive.ubuntu.com trusty-updates/universe Translation-en        
    Hit http://kr.archive.ubuntu.com trusty Release                                
    Hit http://kr.archive.ubuntu.com trusty-backports/main Sources                 
    Hit http://kr.archive.ubuntu.com trusty-backports/restricted Sources           
    Hit http://kr.archive.ubuntu.com trusty-backports/universe Sources             
    Hit http://kr.archive.ubuntu.com trusty-backports/multiverse Sources           
    Hit http://kr.archive.ubuntu.com trusty-backports/main amd64 Packages          
    Hit http://kr.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
    Hit http://kr.archive.ubuntu.com trusty-backports/universe amd64 Packages      
    Hit http://kr.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
    Hit http://kr.archive.ubuntu.com trusty-backports/main i386 Packages           
    Hit http://kr.archive.ubuntu.com trusty-backports/restricted i386 Packages     
    Hit http://kr.archive.ubuntu.com trusty-backports/universe i386 Packages       
    Hit http://kr.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
    Hit http://kr.archive.ubuntu.com trusty-backports/main Translation-en          
    Hit http://kr.archive.ubuntu.com trusty-backports/multiverse Translation-en    
    Hit http://kr.archive.ubuntu.com trusty-backports/restricted Translation-en    
    Hit http://kr.archive.ubuntu.com trusty-backports/universe Translation-en      
    Hit http://us.archive.ubuntu.com vivid InRelease                               
    Hit http://kr.archive.ubuntu.com trusty/main Sources                           
    Hit http://kr.archive.ubuntu.com trusty/restricted Sources                     
    Hit http://kr.archive.ubuntu.com trusty/universe Sources                       
    Hit http://kr.archive.ubuntu.com trusty/multiverse Sources                     
    Hit http://kr.archive.ubuntu.com trusty/main amd64 Packages                    
    Hit http://kr.archive.ubuntu.com trusty/restricted amd64 Packages              
    Hit http://kr.archive.ubuntu.com trusty/universe amd64 Packages                
    Hit http://security.ubuntu.com trusty-security InRelease                       
    Hit http://kr.archive.ubuntu.com trusty/multiverse amd64 Packages              
    Hit http://kr.archive.ubuntu.com trusty/main i386 Packages                     
    Hit http://kr.archive.ubuntu.com trusty/restricted i386 Packages               
    Hit http://kr.archive.ubuntu.com trusty/universe i386 Packages                 
    Hit http://kr.archive.ubuntu.com trusty/multiverse i386 Packages               
    Hit http://us.archive.ubuntu.com vivid/main Sources                            
    Hit http://kr.archive.ubuntu.com trusty/main Translation-en                    
    Hit http://kr.archive.ubuntu.com trusty/multiverse Translation-en              
    Hit http://kr.archive.ubuntu.com trusty/restricted Translation-en              
    Hit http://kr.archive.ubuntu.com trusty/universe Translation-en           
    Hit http://security.ubuntu.com trusty-security/main Sources                    
    Hit http://us.archive.ubuntu.com vivid/universe Sources               
    Hit http://us.archive.ubuntu.com vivid/main amd64 Packages                     
    Hit http://security.ubuntu.com trusty-security/restricted Sources              
    Ign http://kr.archive.ubuntu.com trusty/main Translation-en_US                 
    Get:1 https://download.docker.com trusty InRelease                             
    Ign http://kr.archive.ubuntu.com trusty/multiverse Translation-en_US           
    Ign http://kr.archive.ubuntu.com trusty/restricted Translation-en_US           
    Ign http://kr.archive.ubuntu.com trusty/universe Translation-en_US             
    Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages                 
    Hit http://security.ubuntu.com trusty-security/universe Sources   
    Hit http://us.archive.ubuntu.com vivid/main i386 Packages         
    Hit http://security.ubuntu.com trusty-security/multiverse Sources 
    Hit http://us.archive.ubuntu.com vivid/universe i386 Packages
    Hit http://us.archive.ubuntu.com vivid/main Translation-en     
    Get:2 https://download.docker.com trusty/stable amd64 Packages 
    Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
    Get:3 https://download.docker.com trusty/stable Translation-en_US   
    Hit http://us.archive.ubuntu.com vivid/universe Translation-en                 
    Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
    Get:4 https://download.docker.com trusty/stable Translation-en
    Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
    Get:5 https://download.docker.com trusty/stable Translation-en_US     
    Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages 
    Hit http://security.ubuntu.com trusty-security/main i386 Packages        
    Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
    Get:6 https://download.docker.com trusty/stable Translation-en
    Hit http://security.ubuntu.com trusty-security/universe i386 Packages 
    Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
    Get:7 https://download.docker.com trusty/stable Translation-en_US
    Hit http://security.ubuntu.com trusty-security/main Translation-en      
    Get:8 https://download.docker.com trusty/stable Translation-en
    Hit http://security.ubuntu.com trusty-security/multiverse Translation-en     
    Hit http://security.ubuntu.com trusty-security/restricted Translation-en
    Hit http://security.ubuntu.com trusty-security/universe Translation-en
    Get:9 https://download.docker.com trusty/stable Translation-en_US
    Get:10 https://download.docker.com trusty/stable Translation-en
    Get:11 https://download.docker.com trusty/stable Translation-en_US
    Ign https://download.docker.com trusty/stable Translation-en_US
    Get:12 https://download.docker.com trusty/stable Translation-en
    Ign https://download.docker.com trusty/stable Translation-en                   
    Fetched 15.0 kB in 9s (1,637 B/s)                                              
    Reading package lists... Done

# Install the latest version of Docker, or go to the next step to install a specific version. Any existing installation of Docker is replaced.

    rwoo@rwoo-A610:~$ sudo apt-get install docker-ce
    패키지 목록을 읽는 중입니다... 완료
    의존성 트리를 만드는 중입니다       
    상태 정보를 읽는 중입니다... 완료
    다음 패키지를 더 설치할 것입니다:
      aufs-tools cgroup-lite git git-man liberror-perl
    제안하는 패키지:
      git-daemon-run git-daemon-sysvinit git-doc git-el git-email git-gui gitk
      gitweb git-arch git-bzr git-cvs git-mediawiki git-svn
    다음 새 패키지를 설치할 것입니다:
      aufs-tools cgroup-lite docker-ce git git-man liberror-perl
    0개 업그레이드, 6개 새로 설치, 0개 제거 및 212개 업그레이드 안 함.
    22.5 M바이트 아카이브를 받아야 합니다.
    이 작업 후 111 M바이트의 디스크 공간을 더 사용하게 됩니다.
    계속 하시겠습니까? [Y/n] Y
    받기:1 http://kr.archive.ubuntu.com/ubuntu/ trusty/universe aufs-tools amd64 1:3.2+20130722-1.1 [92.3 kB]
    받기:2 http://kr.archive.ubuntu.com/ubuntu/ trusty/main liberror-perl all 0.17-1.1 [21.1 kB]
    받기:3 http://kr.archive.ubuntu.com/ubuntu/ trusty-updates/main git-man all 1:1.9.1-1ubuntu0.3 [699 kB]
    받기:4 http://kr.archive.ubuntu.com/ubuntu/ trusty-updates/main git amd64 1:1.9.1-1ubuntu0.3 [2,586 kB]
    받기:5 http://kr.archive.ubuntu.com/ubuntu/ trusty/main cgroup-lite all 1.9 [3,918 B]
    내려받기 22.5 M바이트, 소요시간 11초 (2,015 k바이트/초)                        
    Selecting previously unselected package aufs-tools.
    (데이터베이스 읽는중 ...현재 172908개의 파일과 디렉터리가 설치되어 있습니다.)
    Preparing to unpack .../aufs-tools_1%3a3.2+20130722-1.1_amd64.deb ...
    Unpacking aufs-tools (1:3.2+20130722-1.1) ...
    Selecting previously unselected package docker-ce.
    Preparing to unpack .../docker-ce_17.03.0~ce-0~ubuntu-trusty_amd64.deb ...
    Unpacking docker-ce (17.03.0~ce-0~ubuntu-trusty) ...
    Selecting previously unselected package liberror-perl.
    Preparing to unpack .../liberror-perl_0.17-1.1_all.deb ...
    Unpacking liberror-perl (0.17-1.1) ...
    Selecting previously unselected package git-man.
    Preparing to unpack .../git-man_1%3a1.9.1-1ubuntu0.3_all.deb ...
    Unpacking git-man (1:1.9.1-1ubuntu0.3) ...
    Selecting previously unselected package git.
    Preparing to unpack .../git_1%3a1.9.1-1ubuntu0.3_amd64.deb ...
    Unpacking git (1:1.9.1-1ubuntu0.3) ...
    Selecting previously unselected package cgroup-lite.
    Preparing to unpack .../cgroup-lite_1.9_all.deb ...
    Unpacking cgroup-lite (1.9) ...
    Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
    Processing triggers for ureadahead (0.100.0-16) ...
    ureadahead will be reprofiled on next reboot
    aufs-tools (1:3.2+20130722-1.1) 설정하는 중입니다 ...
    docker-ce (17.03.0~ce-0~ubuntu-trusty) 설정하는 중입니다 ...
    docker start/running, process 22887
    liberror-perl (0.17-1.1) 설정하는 중입니다 ...
    git-man (1:1.9.1-1ubuntu0.3) 설정하는 중입니다 ...
    git (1:1.9.1-1ubuntu0.3) 설정하는 중입니다 ...
    cgroup-lite (1.9) 설정하는 중입니다 ...
    cgroup-lite start/running
    Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
    Processing triggers for ureadahead (0.100.0-16) ... 

# Verify that Docker CE or Docker EE is installed correctly by running the hello-world image.

    rwoo@rwoo-A610:~$ docker --version
    Docker version 17.03.0-ce, build 3a232c8

    rwoo@rwoo-A610:~$ sudo groupadd docker
    groupadd: 'docker' 그룹이 이미 있습니다

    rwoo@rwoo-A610:~$ sudo usermod -aG docker $USER

    rwoo@rwoo-A610:~$ sudo reboot

    rwoo@rwoo-A610:~$ docker run hello-world
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
     $ docker run -it ubuntu bash

    Share images, automate workflows, and more with a free Docker ID:
     https://cloud.docker.com/

    For more examples and ideas, visit:
     https://docs.docker.com/engine/userguide/

    rwoo@rwoo-A610:~$ docker images 
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    hello-world         latest              48b5124b2768        2 months ago        1.84 kB
```
