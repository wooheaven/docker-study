# pull gitlab_ce image
```{bash}
$ pwd
/home/rwoo/02_workspace/03_Git_Workspace/Local_GitLab_Workspace	

# /srv/gitlab/data	/var/opt/gitlab		For storing application data
# /srv/gitlab/logs	/var/log/gitlab		For storing logs
# /srv/gitlab/config	/etc/gitlab		For storing the GitLab configuration files

$ sudo rm -rf ./srv
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

# run gitlab_ce contianer
```{bash}
$ sudo docker run \
--detach \
--hostname rwoo-A610 \
--publish 18080:80 \
--publish 220:22 \
--name myGitLab \
--restart always \
--volume `pwd`/srv/gitlab/config:/etc/gitlab \
--volume `pwd`/srv/gitlab/logs:/var/log/gitlab \
--volume `pwd`/srv/gitlab/data:/var/opt/gitlab \
gitlab/gitlab-ce:latest
```

# configure gitlab_ce container
```{bash}
$ docker exec -it myGitLab /bin/bash

root@rwoo-A610:/# vi /etc/gitlab/gitlab.rb

root@rwoo-A610:/# grep -v "#" /etc/gitlab/gitlab.rb | grep "_"
external_url 'http://rwoo-A610:80'
gitlab_rails['gitlab_shell_ssh_port'] = 22

root@rwoo-A610:/# exit

$ docker restart myGitLab
```

# in browser localhost:18080
```{text}
# The very first time you visit GitLab, you will be asked to set up the admin password. 
# After you change it, you can login with username root and the password you set up.
http://localhost:18080

New password : gitlab123123
Username or email : wooheaven79@gmail.com
Password : gitlab123123

username : wooheaven
fullname : wooheaven

create project : Hattrick-Study
```

# in Hattrick-Study repository
```{bash}
$ pwd
/home/rwoo/02_WorkSpace/04_Hattrick/Hattrick-Study

$ git remote -v
github	git@github.com:wooheaven/Hattrick-Study.git (fetch)
github	git@github.com:wooheaven/Hattrick-Study.git (push)
gitlab	git@gitlab.com:wooheaven/Hattrick-Study.git (fetch)
gitlab	git@gitlab.com:wooheaven/Hattrick-Study.git (push)

$ git remote add myGitLab ssh://git@localhost:220/wooheaven/Hattrick-Study.git

$ git fetch --all
Fetching gitlab
Fetching github
Fetching myGitLab
The authenticity of host '[localhost]:220 ([127.0.0.1]:220)' can't be established.
ECDSA key fingerprint is SHA256:HfNe0PXHAgF0sQk3YPREKtJyd1cGR/8/B432u+WSM68.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[localhost]:220' (ECDSA) to the list of known hosts.

$ git push myGitLab master 
Counting objects: 4697, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (4000/4000), done.
Writing objects: 100% (4697/4697), 4.67 MiB | 1.42 MiB/s, done.
Total 4697 (delta 3093), reused 871 (delta 544)
remote: Resolving deltas: 100% (3093/3093), done.
To ssh://localhost:220/wooheaven/Hattrick-Study.git
 * [new branch]      master -> master

$ git branch -avv
* master                  863e94c [gitlab/master] Merge branch '262-2018-06-03-hd' into 'master'
  remotes/github/master   4adbb43 Merge branch '260-2018-06-02-lk-hd' into 'master'
  remotes/gitlab/HEAD     -> gitlab/master
  remotes/gitlab/master   863e94c Merge branch '262-2018-06-03-hd' into 'master'
  remotes/myGitLab/master 863e94c Merge branch '262-2018-06-03-hd' into 'master'
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
