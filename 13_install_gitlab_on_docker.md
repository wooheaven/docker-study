# install docker-ce latest
```{text}
# ref

https://docs.docker.com/engine/installation/linux/ubuntu/#prerequisites

# OS requirements

	rwoo@rwoo-A610:~$ cat /etc/issue
	Ubuntu 14.04.5 LTS \n \l

	rwoo@rwoo-A610:~$ uname -a
	Linux rwoo-A610 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

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
	rwoo@rwoo-A610:~$ sudo apt-get install \
	linux-image-extra-$(uname -r) \
	linux-image-extra-virtual

# Install using the repository

# Set up the repository (Before you install Docker for the first time on a new host machine, you need to set up the Docker repository.)

# Docker CE

# Install packages to allow apt to use a repository over HTTPS:

	rwoo@rwoo-A610:~$ sudo apt-get install \
	>     apt-transport-https \
	>     ca-certificates \
	>     curl \
	>     software-properties-common
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	ca-certificates is already the newest version.
	Some packages could not be installed. This may mean that you have
	requested an impossible situation or if you are using the unstable
	distribution that some required packages have not yet been created
	or been moved out of Incoming.
	The following information may help to resolve the situation:

	The following packages have unmet dependencies:
	apt-transport-https : Depends: libapt-pkg4.12 (>= 1.0.9.7ubuntu4) but 1.0.1ubuntu2.14 is to be installed
	Depends: libstdc++6 (>= 4.9) but 4.8.2-19ubuntu1 is to be installed
	E: Unable to correct problems, you have held broken packages.

	rwoo@rwoo-A610:~$ sudo aptitude install apt-transport-https
	The following packages will be REMOVED:  
	aufs-tools{u} cgroup-lite{u} 
	The following packages will be upgraded:
	apt-transport-https libapt-pkg4.12 libstdc++6{b} 
	3 packages upgraded, 0 newly installed, 2 to remove and 1505 not upgraded.
	Need to get 988 kB of archives. After unpacking 58.4 kB will be freed.
	The following packages have unmet dependencies:
	libstdc++6 : Depends: gcc-4.9-base (= 4.9.2-10ubuntu13) but 4.9.3-0ubuntu4 is installed.
	open: 645; closed: 595; defer: 579; conflict: 969o
	The following actions will resolve these dependencies:

	Keep the following packages at their current version:
	1)     apt-transport-https [1.0.1ubuntu2.14 (now)]        
	2)     libapt-pkg4.12 [1.0.1ubuntu2.14 (now)]             
	3)     libstdc++6 [4.8.2-19ubuntu1 (now, trusty)]         

	Accept this solution? [Y/n/q/?] n
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	The following actions will resolve these dependencies:

	Remove the following packages:                       
	1)     apt-transport-https                                
	2)     opera-stable                                       

	Keep the following packages at their current version:
	3)     libapt-pkg4.12 [1.0.1ubuntu2.14 (now)]             
	4)     libstdc++6 [4.8.2-19ubuntu1 (now, trusty)]         

	Leave the following dependencies unresolved:         
	5)     ubuntu-standard recommends apt-transport-https 


	Accept this solution? [Y/n/q/?] n
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	Internal error: found 2 (choice -> promotion) mappings for a single choice.
	The following actions will resolve these dependencies:

	Install the following packages:                                                  
	1)     gcc-5-base [5.1~rc1-0ubuntu1 (vivid)]                                          

	Upgrade the following packages:                                                  
	2)     libgcc1 [1:4.9.3-0ubuntu4 (now, trusty-updates) -> 1:5.1~rc1-0ubuntu1 (vivid)] 

	Downgrade the following packages:                                                
	3)     gcc-4.9-base [4.9.3-0ubuntu4 (now, trusty-updates) -> 4.9.2-10ubuntu13 (vivid)]



	Accept this solution? [Y/n/q/?] Y
	The following packages will be DOWNGRADED:
	gcc-4.9-base 
	The following NEW packages will be installed:
	gcc-5-base{a} 
	The following packages will be REMOVED:
	aufs-tools{u} cgroup-lite{u} 
	The following packages will be upgraded:
	apt-transport-https libapt-pkg4.12 libgcc1 libstdc++6 
	4 packages upgraded, 1 newly installed, 1 downgraded, 2 to remove and 1504 not upgraded.
	Need to get 1,057 kB of archives. After unpacking 22.5 kB will be used.
	Do you want to continue? [Y/n/?] Y
	Get: 1 http://us.archive.ubuntu.com/ubuntu/ vivid/main gcc-5-base amd64 5.1~rc1-0ubuntu1 [14.3 kB]
	Get: 2 http://us.archive.ubuntu.com/ubuntu/ vivid/main libgcc1 amd64 1:5.1~rc1-0ubuntu1 [39.1 kB]
	Get: 3 http://us.archive.ubuntu.com/ubuntu/ vivid/main gcc-4.9-base amd64 4.9.2-10ubuntu13 [15.9 kB]
	Get: 4 http://us.archive.ubuntu.com/ubuntu/ vivid/main libstdc++6 amd64 4.9.2-10ubuntu13 [278 kB]
	Get: 5 http://us.archive.ubuntu.com/ubuntu/ vivid/main libapt-pkg4.12 amd64 1.0.9.7ubuntu4 [682 kB]
	Get: 6 http://us.archive.ubuntu.com/ubuntu/ vivid/main apt-transport-https amd64 1.0.9.7ubuntu4 [27.3 kB]
	Fetched 1,057 kB in 2s (386 kB/s)              
	(Reading database ... 199744 files and directories currently installed.)
		Removing aufs-tools (1:3.2+20130722-1.1) ...
		Removing cgroup-lite (1.9) ...
		cgroup-lite stop/waiting
		Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
		Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
		Selecting previously unselected package gcc-5-base:amd64.
	(Reading database ... 199685 files and directories currently installed.)
		Preparing to unpack .../gcc-5-base_5.1~rc1-0ubuntu1_amd64.deb ...
		Unpacking gcc-5-base:amd64 (5.1~rc1-0ubuntu1) ...
		Setting up gcc-5-base:amd64 (5.1~rc1-0ubuntu1) ...
	(Reading database ... 199692 files and directories currently installed.)
		Preparing to unpack .../libgcc1_1%3a5.1~rc1-0ubuntu1_amd64.deb ...
		Unpacking libgcc1:amd64 (1:5.1~rc1-0ubuntu1) over (1:4.9.3-0ubuntu4) ...
		Setting up libgcc1:amd64 (1:5.1~rc1-0ubuntu1) ...
		Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
		dpkg: warning: downgrading gcc-4.9-base:amd64 from 4.9.3-0ubuntu4 to 4.9.2-10ubuntu13
	(Reading database ... 199692 files and directories currently installed.)
		Preparing to unpack .../gcc-4.9-base_4.9.2-10ubuntu13_amd64.deb ...
		Unpacking gcc-4.9-base:amd64 (4.9.2-10ubuntu13) over (4.9.3-0ubuntu4) ...
		Setting up gcc-4.9-base:amd64 (4.9.2-10ubuntu13) ...
	(Reading database ... 199692 files and directories currently installed.)
		Preparing to unpack .../libstdc++6_4.9.2-10ubuntu13_amd64.deb ...
		Unpacking libstdc++6:amd64 (4.9.2-10ubuntu13) over (4.8.2-19ubuntu1) ...
		Setting up libstdc++6:amd64 (4.9.2-10ubuntu13) ...
		Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
	(Reading database ... 199704 files and directories currently installed.)
		Preparing to unpack .../libapt-pkg4.12_1.0.9.7ubuntu4_amd64.deb ...
		Unpacking libapt-pkg4.12:amd64 (1.0.9.7ubuntu4) over (1.0.1ubuntu2.14) ...
		Setting up libapt-pkg4.12:amd64 (1.0.9.7ubuntu4) ...
		Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
	(Reading database ... 199704 files and directories currently installed.)
		Preparing to unpack .../apt-transport-https_1.0.9.7ubuntu4_amd64.deb ...
		Unpacking apt-transport-https (1.0.9.7ubuntu4) over (1.0.1ubuntu2.14) ...
		Setting up apt-transport-https (1.0.9.7ubuntu4) ...

		Current status: 1504 updates [-5].

	rwoo@rwoo-A610:~$ sudo apt-get install \
	>     apt-transport-https \
	>     ca-certificates \
	>     curl \
	>     software-properties-common
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	ca-certificates is already the newest version.
	apt-transport-https is already the newest version.
	The following packages were automatically installed and are no longer required:
	linux-image-3.13.0-96-generic linux-image-extra-3.13.0-96-generic
	Use 'apt-get autoremove' to remove them.
	The following extra packages will be installed:
	libcurl3 libgmp10 libgnutls-deb0-28 libhogweed2 libnettle4 libp11-kit0
	librtmp1 libtasn1-6 p11-kit-modules python3-software-properties
	software-properties-gtk
	Suggested packages:
	gnutls-bin
	The following NEW packages will be installed:
	libgnutls-deb0-28 libhogweed2 librtmp1
	The following packages will be upgraded:
	curl libcurl3 libgmp10 libnettle4 libp11-kit0 libtasn1-6 p11-kit-modules
	python3-software-properties software-properties-common
	software-properties-gtk
	10 upgraded, 3 newly installed, 0 to remove and 1495 not upgraded.
	Need to get 1,619 kB of archives.
	After this operation, 1,929 kB of additional disk space will be used.
	Do you want to continue? [Y/n] Y
	Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid/main libgmp10 amd64 2:6.0.0+dfsg-6ubuntu1 [241 kB]
	Get:2 http://us.archive.ubuntu.com/ubuntu/ vivid/main libnettle4 amd64 2.7.1-5 [107 kB]
	Get:3 http://us.archive.ubuntu.com/ubuntu/ vivid/main libhogweed2 amd64 2.7.1-5 [125 kB]
	Get:4 http://us.archive.ubuntu.com/ubuntu/ vivid/main libtasn1-6 amd64 4.2-2ubuntu1 [42.4 kB]
	Get:5 http://us.archive.ubuntu.com/ubuntu/ vivid/main p11-kit-modules amd64 0.20.7-1 [73.1 kB]
	Get:6 http://us.archive.ubuntu.com/ubuntu/ vivid/main libp11-kit0 amd64 0.20.7-1 [77.1 kB]
	Get:7 http://us.archive.ubuntu.com/ubuntu/ vivid/main libgnutls-deb0-28 amd64 3.3.8-3ubuntu3 [515 kB]
	Get:8 http://us.archive.ubuntu.com/ubuntu/ vivid/main librtmp1 amd64 2.4+20131018.git79459a2-5 [54.7 kB]
	Get:9 http://us.archive.ubuntu.com/ubuntu/ vivid/main curl amd64 7.38.0-3ubuntu2 [129 kB]
	Get:10 http://us.archive.ubuntu.com/ubuntu/ vivid/main libcurl3 amd64 7.38.0-3ubuntu2 [180 kB]
	Get:11 http://us.archive.ubuntu.com/ubuntu/ vivid/main software-properties-common all 0.96.4 [9,492 B]
	Get:12 http://us.archive.ubuntu.com/ubuntu/ vivid/main software-properties-gtk all 0.96.4 [46.8 kB]
	Get:13 http://us.archive.ubuntu.com/ubuntu/ vivid/main python3-software-properties all 0.96.4 [19.4 kB]
	Fetched 1,619 kB in 5s (289 kB/s)                  
	(Reading database ... 199704 files and directories currently installed.)
		Preparing to unpack .../libgmp10_2%3a6.0.0+dfsg-6ubuntu1_amd64.deb ...
		Unpacking libgmp10:amd64 (2:6.0.0+dfsg-6ubuntu1) over (2:5.1.3+dfsg-1ubuntu1) ...
		Preparing to unpack .../libnettle4_2.7.1-5_amd64.deb ...
		Unpacking libnettle4:amd64 (2.7.1-5) over (2.7.1-1ubuntu0.1) ...
		Selecting previously unselected package libhogweed2:amd64.
		Preparing to unpack .../libhogweed2_2.7.1-5_amd64.deb ...
		Unpacking libhogweed2:amd64 (2.7.1-5) ...
		Preparing to unpack .../libtasn1-6_4.2-2ubuntu1_amd64.deb ...
		Unpacking libtasn1-6:amd64 (4.2-2ubuntu1) over (3.4-3ubuntu0.4) ...
		Preparing to unpack .../p11-kit-modules_0.20.7-1_amd64.deb ...
		Unpacking p11-kit-modules:amd64 (0.20.7-1) over (0.20.2-2ubuntu2) ...
		Preparing to unpack .../libp11-kit0_0.20.7-1_amd64.deb ...
		Unpacking libp11-kit0:amd64 (0.20.7-1) over (0.20.2-2ubuntu2) ...
		Selecting previously unselected package libgnutls-deb0-28:amd64.
		Preparing to unpack .../libgnutls-deb0-28_3.3.8-3ubuntu3_amd64.deb ...
		Unpacking libgnutls-deb0-28:amd64 (3.3.8-3ubuntu3) ...
		Selecting previously unselected package librtmp1:amd64.
		Preparing to unpack .../librtmp1_2.4+20131018.git79459a2-5_amd64.deb ...
		Unpacking librtmp1:amd64 (2.4+20131018.git79459a2-5) ...
		Preparing to unpack .../curl_7.38.0-3ubuntu2_amd64.deb ...
		Unpacking curl (7.38.0-3ubuntu2) over (7.35.0-1ubuntu2.8) ...
		Preparing to unpack .../libcurl3_7.38.0-3ubuntu2_amd64.deb ...
		Unpacking libcurl3:amd64 (7.38.0-3ubuntu2) over (7.35.0-1ubuntu2.8) ...
		Preparing to unpack .../software-properties-common_0.96.4_all.deb ...
		Unpacking software-properties-common (0.96.4) over (0.92.37.7) ...
		Preparing to unpack .../software-properties-gtk_0.96.4_all.deb ...
		Unpacking software-properties-gtk (0.96.4) over (0.92.37.7) ...
		Preparing to unpack .../python3-software-properties_0.96.4_all.deb ...
		Unpacking python3-software-properties (0.96.4) over (0.92.37.7) ...
		Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
		Processing triggers for hicolor-icon-theme (0.13-1) ...
		Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
		Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
		Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
		Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
		Rebuilding /usr/share/applications/bamf-2.index...
		Processing triggers for mime-support (3.54ubuntu1.1) ...
		Setting up libgmp10:amd64 (2:6.0.0+dfsg-6ubuntu1) ...
		Setting up libnettle4:amd64 (2.7.1-5) ...
		Setting up libhogweed2:amd64 (2.7.1-5) ...
		Setting up libtasn1-6:amd64 (4.2-2ubuntu1) ...
		Setting up libp11-kit0:amd64 (0.20.7-1) ...
		Setting up p11-kit-modules:amd64 (0.20.7-1) ...
		Setting up libgnutls-deb0-28:amd64 (3.3.8-3ubuntu3) ...
		Setting up librtmp1:amd64 (2.4+20131018.git79459a2-5) ...
		Setting up libcurl3:amd64 (7.38.0-3ubuntu2) ...
		Setting up curl (7.38.0-3ubuntu2) ...
		Setting up python3-software-properties (0.96.4) ...
		Setting up software-properties-common (0.96.4) ...
		Setting up software-properties-gtk (0.96.4) ...
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

	rwoo@rwoo-A610:~$ sudo add-apt-repository \
	>    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
	>    $(lsb_release -cs) \
	>    stable"

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
	etched 15.0 kB in 9s (1,637 B/s)                                              
	Reading package lists... Done

# Install the latest version of Docker, or go to the next step to install a specific version. Any existing installation of Docker is replaced.

	rwoo@rwoo-A610:~$ sudo apt-get install docker-ce
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	The following packages were automatically installed and are no longer required:
	linux-image-3.13.0-96-generic linux-image-extra-3.13.0-96-generic
	Use 'apt-get autoremove' to remove them.
	Recommended packages:
	apparmor
	The following NEW packages will be installed:
	docker-ce
	0 upgraded, 1 newly installed, 0 to remove and 1445 not upgraded.
	4 not fully installed or removed.
	Need to get 0 B/19.1 MB of archives.
	After this operation, 88.6 MB of additional disk space will be used.
	Selecting previously unselected package docker-ce.
	(Reading database ... 199038 files and directories currently installed.)
		Preparing to unpack .../docker-ce_17.03.0~ce-0~ubuntu-trusty_amd64.deb ...
		Unpacking docker-ce (17.03.0~ce-0~ubuntu-trusty) ...
		Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
		Processing triggers for ureadahead (0.100.0-19) ...
		Setting up cups-daemon (2.0.2-1ubuntu3) ...
		update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match cups Default-Stop values (1)
		/usr/sbin/invoke-rc.d: 1: /usr/sbin/invoke-rc.d: /sbin/runlevel: not found
		start: Job failed to start
		invoke-rc.d: initscript cups, action "start" failed.
	dpkg: error processing package cups-daemon (--configure):
		subprocess installed post-installation script returned error exit status 1
		Setting up fontconfig (2.11.1-0ubuntu6) ...
		Regenerating fonts cache... failed.
		See /var/log/fontconfig.log for more information.
	dpkg: error processing package fontconfig (--configure):
		subprocess installed post-installation script returned error exit status 1
	dpkg: dependency problems prevent configuration of cups-core-drivers:
		cups-core-drivers depends on cups-daemon (>= 2.0.2-1ubuntu3); however:
		Package cups-daemon is not configured yet.

	dpkg: error processing package cups-core-drivers (--configure):
		dependency problems - leaving unconfigured
	dpkg: dependency problems prevent configuration of cups:
		cups depends on cups-core-drivers (>= 2.0.2-1ubuntu3); however:
	Package cups-core-drivers is not configured yet.
		cups depends on cups-daemon (>= 2.0.2-1ubuntu3); however:
	Package cups-daemon is not configured yet.

	dpkg: error processing package cups (--configure):
		dependency problems - leaving unconfigured
	Setting up docker-ce (17.03.0~ce-0~ubuntu-trusty) ...
		No apport report written because the error message indicates its a followup error from a previous failure.
		No apport report written because MaxReports is reached already
	/usr/sbin/invoke-rc.d: 1: /usr/sbin/invoke-rc.d: /sbin/runlevel: not found
	docker start/running, process 15192
	Processing triggers for ureadahead (0.100.0-19) ...
	Errors were encountered while processing:
		cups-daemon
		fontconfig
		cups-core-drivers
		cups
	E: Sub-process /usr/bin/dpkg returned an error code (1)

	rwoo@rwoo-A610:~$ sudo apt-get purge cups-daemon
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	The following packages were automatically installed and are no longer required:
	cups-browsed cups-server-common hplip-data libart-2.0-2 libcupscgi1
	libcupsmime1 libgutenprint2 libhpmud0 libsane-hpaio libsensors4 libsnmp-base
	libsnmp30 python-pexpect python-renderpm python-reportlab
	python-reportlab-accel python3-pexpect python3-pil python3-reportlab
	python3-reportlab-accel ssl-cert
	Use 'apt-get autoremove' to remove them.
	The following packages will be REMOVED:
	cups-core-drivers* cups-daemon*
	0 upgraded, 0 newly installed, 2 to remove and 1424 not upgraded.
	2 not fully installed or removed.
	After this operation, 1,153 kB disk space will be freed.
	Do you want to continue? [Y/n] Y
	(Reading database ... 194529 files and directories currently installed.)
		Removing cups-core-drivers (2.0.2-1ubuntu3) ...
		Removing cups-daemon (2.0.2-1ubuntu3) ...
		/usr/sbin/invoke-rc.d: 1: /usr/sbin/invoke-rc.d: /sbin/runlevel: not found
		Purging configuration files for cups-daemon (2.0.2-1ubuntu3) ...
		Processing triggers for man-db (2.6.7.1-1ubuntu1) ...

	rwoo@rwoo-A610:~$ sudo apt-get purge cups
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	Package 'cups' is not installed, so not removed
	The following packages were automatically installed and are no longer required:
	cups-browsed cups-server-common hplip-data libart-2.0-2 libcupscgi1
		libcupsmime1 libgutenprint2 libhpmud0 libsane-hpaio libsensors4 libsnmp-base
		libsnmp30 python-pexpect python-renderpm python-reportlab
		python-reportlab-accel python3-pexpect python3-pil python3-reportlab
		python3-reportlab-accel ssl-cert
	Use 'apt-get autoremove' to remove them.
		0 upgraded, 0 newly installed, 0 to remove and 1424 not upgraded.
		rwoo@rwoo-A610:~$ sudo apt-get autoremove
		Reading package lists... Done
		Building dependency tree       
		Reading state information... Done
		The following packages will be REMOVED:
		cups-browsed cups-server-common hplip-data libart-2.0-2 libcupscgi1
		libcupsmime1 libgutenprint2 libhpmud0 libsane-hpaio libsensors4 libsnmp-base
		libsnmp30 python-pexpect python-renderpm python-reportlab
		python-reportlab-accel python3-pexpect python3-pil python3-reportlab
		python3-reportlab-accel ssl-cert
		0 upgraded, 0 newly installed, 21 to remove and 1416 not upgraded.
		After this operation, 33.7 MB disk space will be freed.
		Do you want to continue? [Y/n] Y
	(Reading database ... 194474 files and directories currently installed.)
		Removing cups-browsed (1.0.52-0ubuntu1.7) ...
		/usr/sbin/invoke-rc.d: 1: /usr/sbin/invoke-rc.d: /sbin/runlevel: not found
		cups-browsed stop/waiting
		Removing cups-server-common (2.0.2-1ubuntu3) ...
		Removing hplip-data (3.15.2-0ubuntu4) ...
		Removing python-renderpm (3.0-1build1) ...
		Removing libart-2.0-2:amd64 (2.3.21-2) ...
		Removing libcupscgi1:amd64 (2.0.2-1ubuntu3) ...
		Removing libcupsmime1:amd64 (2.0.2-1ubuntu3) ...
		Removing libgutenprint2 (5.2.10-3build1) ...
		Removing libsane-hpaio (3.15.2-0ubuntu4) ...
		Removing libhpmud0 (3.15.2-0ubuntu4) ...
		Removing libsnmp30:amd64 (5.7.2~dfsg-8.1ubuntu5) ...
		Removing libsensors4:amd64 (1:3.3.4-2ubuntu1) ...
		Removing libsnmp-base (5.7.2~dfsg-8.1ubuntu3.2) ...
		Removing python-pexpect (3.1-1ubuntu0.1) ...
		Removing python-reportlab (3.0-1build1) ...
		Removing python-reportlab-accel (3.0-1build1) ...
		Removing python3-pexpect (3.2-1) ...
		Removing python3-pil:amd64 (2.7.0-1) ...
		Removing python3-reportlab (3.1.44-1) ...
		Removing python3-reportlab-accel:amd64 (3.1.44-1) ...
		Removing ssl-cert (1.0.33) ...
		Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
		Processing triggers for doc-base (0.10.5) ...
		Possible precedence issue with control flow operator at /usr/share/perl5/Debian/DocBase/DB.pm line 101.
		Processing 1 removed doc-base file...
		Processing triggers for libc-bin (2.19-0ubuntu6.9) ...

	rwoo@rwoo-A610:~$ sudo apt-get autoremove
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	The following packages will be REMOVED:
	cups-browsed cups-server-common hplip-data libart-2.0-2 libcupscgi1
	libcupsmime1 libgutenprint2 libhpmud0 libsane-hpaio libsensors4 libsnmp-base
	libsnmp30 python-pexpect python-renderpm python-reportlab
	python-reportlab-accel python3-pexpect python3-pil python3-reportlab
	python3-reportlab-accel ssl-cert
	0 upgraded, 0 newly installed, 21 to remove and 1416 not upgraded.
	After this operation, 33.7 MB disk space will be freed.
	Do you want to continue? [Y/n] Y
	(Reading database ... 194474 files and directories currently installed.)
	Removing cups-browsed (1.0.52-0ubuntu1.7) ...
	/usr/sbin/invoke-rc.d: 1: /usr/sbin/invoke-rc.d: /sbin/runlevel: not found
	cups-browsed stop/waiting
	Removing cups-server-common (2.0.2-1ubuntu3) ...
	Removing hplip-data (3.15.2-0ubuntu4) ...
	Removing python-renderpm (3.0-1build1) ...
	Removing libart-2.0-2:amd64 (2.3.21-2) ...
	Removing libcupscgi1:amd64 (2.0.2-1ubuntu3) ...
	Removing libcupsmime1:amd64 (2.0.2-1ubuntu3) ...
	Removing libgutenprint2 (5.2.10-3build1) ...
	Removing libsane-hpaio (3.15.2-0ubuntu4) ...
	Removing libhpmud0 (3.15.2-0ubuntu4) ...
	Removing libsnmp30:amd64 (5.7.2~dfsg-8.1ubuntu5) ...
	Removing libsensors4:amd64 (1:3.3.4-2ubuntu1) ...
	Removing libsnmp-base (5.7.2~dfsg-8.1ubuntu3.2) ...
	Removing python-pexpect (3.1-1ubuntu0.1) ...
	Removing python-reportlab (3.0-1build1) ...
	Removing python-reportlab-accel (3.0-1build1) ...
	Removing python3-pexpect (3.2-1) ...
	Removing python3-pil:amd64 (2.7.0-1) ...
	Removing python3-reportlab (3.1.44-1) ...
	Removing python3-reportlab-accel:amd64 (3.1.44-1) ...
	Removing ssl-cert (1.0.33) ...
	Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
	Processing triggers for doc-base (0.10.5) ...
	Possible precedence issue with control flow operator at /usr/share/perl5/Debian/DocBase/DB.pm line 101.
	Processing 1 removed doc-base file...
	Processing triggers for libc-bin (2.19-0ubuntu6.9) ...

	rwoo@rwoo-A610:~$ sudo apt-get install docker-ce
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	docker-ce is already the newest version.
	0 upgraded, 0 newly installed, 0 to remove and 1416 not upgraded.

# Verify that Docker CE or Docker EE is installed correctly by running the hello-world image.

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

# docker-ce image
```{text}
	rwoo@rwoo-A610:~/02_WorkSpace/03_Git_workspace/gitlab-ce$ mkdir srv
	rwoo@rwoo-A610:~/02_WorkSpace/03_Git_workspace/gitlab-ce$ mkdir srv/gitlab
	rwoo@rwoo-A610:~/02_WorkSpace/03_Git_workspace/gitlab-ce$ mkdir srv/gitlab/config
	rwoo@rwoo-A610:~/02_WorkSpace/03_Git_workspace/gitlab-ce$ mkdir srv/gitlab/logs
	rwoo@rwoo-A610:~/02_WorkSpace/03_Git_workspace/gitlab-ce$ mkdir srv/gitlab/data
	rwoo@rwoo-A610:~/02_WorkSpace/03_Git_workspace/gitlab-ce$ docker pull gitlab/gitlab-ce:latest
	latest: Pulling from gitlab/gitlab-ce
	d54efb8db41d: Pull complete 
	f8b845f45a87: Pull complete 
	e8db7bf7c39f: Pull complete 
	9654c40e9079: Pull complete 
	6d9ef359eaaa: Pull complete 
	9f03761cbae1: Pull complete 
	eda25921fba9: Pull complete 
	2705b72c3b47: Pull complete 
	d504b68e1ccc: Pull complete 
	43faeb1d27a2: Pull complete 
	a6892e0eba8d: Pull complete 
	Digest: sha256:9bc6001bcf36362d93b254e702b06ef16c7657fc7f5f8d7ea24b981b041b6ae9
	Status: Downloaded newer image for gitlab/gitlab-ce:latest
	
	rwoo@rwoo-A610:~/02_WorkSpace/03_Git_workspace/gitlab-ce$ docker images 
	REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
	gitlab/gitlab-ce    latest              b912fec48b7c        7 days ago          1.21 GB
	hello-world         latest              48b5124b2768        2 months ago        1.84 kB
```

# docker run
```{text}
sudo docker run --detach \
--hostname gitlab.example.com \
--publish 443:443 --publish 80:80 --publish 220:22 \
--name gitlab \
--restart always \
--volume `pwd`/srv/gitlab/config:/etc/gitlab \
--volume `pwd`/srv/gitlab/logs:/var/log/gitlab \
--volume `pwd`/srv/gitlab/data:/var/opt/gitlab \
 gitlab/gitlab-ce:latest
```

# The very first time you visit GitLab, you will be asked to set up the admin password. 
# After you change it, you can login with username root and the password you set up.
```{text}
http://localhost
```
