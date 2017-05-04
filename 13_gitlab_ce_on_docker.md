# docker-ce image
```{bash}
$ pwd
/home/rwoo/02_workspace/03_Git_Workspace/Local_GitLab_Workspace	

# /srv/gitlab/data	/var/opt/gitlab		For storing application data
# /srv/gitlab/logs	/var/log/gitlab		For storing logs
# /srv/gitlab/config	/etc/gitlab		For storing the GitLab configuration files

$ mkdir srv
$ mkdir srv/gitlab
$ mkdir srv/gitlab/config
$ mkdir srv/gitlab/logs
$ mkdir srv/gitlab/data
$ docker pull gitlab/gitlab-ce:latest
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
	
$ docker images 
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
gitlab/gitlab-ce    latest              b912fec48b7c        7 days ago          1.21 GB
```

# docker run
```{bash}
$ sudo docker run --detach \
--hostname gitlab.example.com \
--publish 443:443 --publish 80:80 --publish 220:22 \
--name gitlab \
--restart always \
--volume `pwd`/srv/gitlab/config:/etc/gitlab \
--volume `pwd`/srv/gitlab/logs:/var/log/gitlab \
--volume `pwd`/srv/gitlab/data:/var/opt/gitlab \
 gitlab/gitlab-ce:latest
```

# in browser
```{text}
# The very first time you visit GitLab, you will be asked to set up the admin password. 
# After you change it, you can login with username root and the password you set up.
http://localhost
```

# in container console
```{bash}
$ sudo docker exec -it gitlab /bin/bash

root@gitlab:/# echo $0
/bin/bash

root@gitlab:/# pwd
/

root@gitlab:/# ll
total 80
drwxr-xr-x  51 root root 4096 May  1 14:50 ./
drwxr-xr-x  51 root root 4096 May  1 14:50 ../
-rwxr-xr-x   1 root root    0 May  1 14:50 .dockerenv*
-rw-r--r--   1 root root  182 May  1 13:11 RELEASE
drwxr-xr-x   2 root root 4096 May  1 13:12 assets/
drwxr-xr-x   2 root root 4096 May  1 13:12 bin/
drwxr-xr-x   2 root root 4096 Apr 12  2016 boot/
drwxr-xr-x   5 root root  340 May  1 14:50 dev/
drwxr-xr-x  66 root root 4096 May  1 14:50 etc/
drwxr-xr-x   2 root root 4096 Apr 12  2016 home/
drwxr-xr-x  10 root root 4096 May  1 13:12 lib/
drwxr-xr-x   2 root root 4096 Apr 17 20:30 lib64/
drwxr-xr-x   2 root root 4096 Apr 17 20:30 media/
drwxr-xr-x   2 root root 4096 Apr 17 20:30 mnt/
drwxr-xr-x   4 root root 4096 May  1 14:50 opt/
dr-xr-xr-x 357 root root    0 May  1 14:50 proc/
drwx------   2 root root 4096 Apr 17 20:31 root/
drwxr-xr-x   7 root root 4096 May  1 14:50 run/
drwxr-xr-x   2 root root 4096 Apr 24 22:57 sbin/
drwxr-xr-x   2 root root 4096 Apr 17 20:30 srv/
dr-xr-xr-x  13 root root    0 May  1 14:50 sys/
drwxrwxrwt   2 root root 4096 May  1 14:51 tmp/
drwxr-xr-x  17 root root 4096 May  1 13:12 usr/
drwxr-xr-x  19 root root 4096 May  1 13:12 var/
```

# start or stop gitlab container
```{bash}
$ sudo docker start gitlab

$ sudo docker stop gitlab
```

# reference
```{text}
https://docs.gitlab.com/omnibus/docker/#prerequisites
```
