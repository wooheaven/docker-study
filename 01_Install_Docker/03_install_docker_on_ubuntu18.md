```
$ sudo apt update

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
$ apt-cache policy docker-ce
docker-ce:
  Installed: (none)
  Candidate: 5:19.03.7~3-0~ubuntu-bionic
  Version table:
     5:19.03.7~3-0~ubuntu-bionic 500
        500 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages
     5:19.03.6~3-0~ubuntu-bionic 500
        500 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages
     5:19.03.5~3-0~ubuntu-bionic 500
        500 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages
     5:19.03.4~3-0~ubuntu-bionic 500

$ sudo apt install docker-ce
$ sudo systemctl status docker
● docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2020-03-05 17:08:59 KST; 21s ago
     Docs: https://docs.docker.com
 Main PID: 5964 (dockerd)
    Tasks: 17
   CGroup: /system.slice/docker.service
           └─5964 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock

 3월 05 17:08:58 bigdata dockerd[5964]: time="2020-03-05T17:08:58.041623628+09:00" level=warning msg=
 3월 05 17:08:58 bigdata dockerd[5964]: time="2020-03-05T17:08:58.041640372+09:00" level=warning msg=
 3월 05 17:08:58 bigdata dockerd[5964]: time="2020-03-05T17:08:58.041656805+09:00" level=warning msg=
 3월 05 17:08:58 bigdata dockerd[5964]: time="2020-03-05T17:08:58.042118017+09:00" level=info msg="Lo
 3월 05 17:08:58 bigdata dockerd[5964]: time="2020-03-05T17:08:58.449284670+09:00" level=info msg="De
 3월 05 17:08:58 bigdata dockerd[5964]: time="2020-03-05T17:08:58.680976963+09:00" level=info msg="Lo
 3월 05 17:08:58 bigdata dockerd[5964]: time="2020-03-05T17:08:58.886294455+09:00" level=info msg="Do
 3월 05 17:08:58 bigdata dockerd[5964]: time="2020-03-05T17:08:58.886543303+09:00" level=info msg="Da
 3월 05 17:08:59 bigdata dockerd[5964]: time="2020-03-05T17:08:59.252283083+09:00" level=info msg="AP
 3월 05 17:08:59 bigdata systemd[1]: Started Docker Application Container Engine.

$ sudo groupadd docker
$ sudo usermod -aG docker $USER
$ sudo reboot
```
