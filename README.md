# [docker html document in korean](http://www.pyrasis.com/docker.html)

# [docker install : docker CE on Ubuntu14.04](00_docker_install.md)
```{bash}
$ sudo apt-get install docker-ce
$ docker -v
```

# [docker images](01_docker_images.md)
```{bash}
$ docker images
```

# [docker search](02_docker_search.md)
```{bash}
$ docker search ubuntu
```

# [docker pull](03_docker_pull.md)
```{bash}
$ docker pull
```

# [docker run](04_docker_run.md)
```{bash}
$ docker run -it -p 127.0.0.1:9999:9999 -v /Users/rwoo/2_Workspace/17_Python_workspace/Python2.7-Study:/home/python_workspace --name="py27study" ubuntu:14.04-python2.7 /bin/bash
```

# [docker ps](05_docker_ps.md)
```{bash}
$ docker ps
$ docker ps -a
```

# [docker port](06_docker_port.md)
```{bash}
$ docker port
```

# [docker attach](07_docker_attach.md)
```{bash}
$ docker attach 42ff601ded9a
```

# [docker start](08_docker_start.md)
```{bash}
$ docker start 42ff601ded9a
```

# [docker exit](09_docker_exit.md)
```{bash}
root@42ff601ded9a:/# exit
root@14asdfj8ad83:/# Ctl + P + Q
```

# [docker commit](10_docker_commit.md)
```{bash}
$ docker commit 42ff601ded9a ubuntu:14.04-python2.7
```

# [BusyBox : The Swiss Army Knife of Embedded Linux](11_BusyBox_on_docker.md)
```{bash}
$ docker create -v /var/lib/postgresql/data --name postgres9.3.6-data busybox
```

# [docker volumn](12_docker_volumn.md)
```{bash}
$ docker create -v `pwd`/testFolder:/tmp/testFolder --name dataContainer busybox
$ docker run -it --name localContainer -d --volumes-from dataContainer busybox:latest sh
```

# [gitlab_on_docker](13_install_gitlab_on_docker.md)
```{bash}
$ docker start gitlab
http://localhost
$ docker stop gitlab
```
