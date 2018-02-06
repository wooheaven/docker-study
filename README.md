# [docker html document in korean](http://www.pyrasis.com/docker.html)

# [docker install : docker-ce on Ubuntu14](00_docker_command/00_install_docker/00_on_ubuntu14.md)
# [docker install : docker-ce on Ubuntu16](00_docker_command/00_install_docker/01_on_ubuntu16.md)

# [docker images](00_docker_command/01_docker_images.md)
```{bash}
$ docker images
```

# [docker search](00_docker_command/02_docker_search.md)
```{bash}
$ docker search ubuntu
```

# [docker pull](00_docker_command/03_docker_pull.md)
```{bash}
$ docker pull
```

# [docker run](00_docker_command/04_docker_run.md)
```{bash}
$ docker run -it -p 127.0.0.1:9999:9999 -v /Users/rwoo/2_Workspace/17_Python_workspace/Python2.7-Study:/home/python_workspace --name="py27study" ubuntu:14.04-python2.7 /bin/bash
```

# [docker ps](00_docker_command/05_docker_ps.md)
```{bash}
$ docker ps
$ docker ps -a
```

# [docker port](00_docker_command/06_docker_port.md)
```{bash}
$ docker port
```

# [docker attach](00_docker_command/07_docker_attach.md)
```{bash}
$ docker attach 42ff601ded9a
```

# [docker start](00_docker_command/08_docker_start.md)
```{bash}
$ docker start 42ff601ded9a
```

# [docker exit](00_docker_command/09_docker_exit.md)
```{bash}
root@42ff601ded9a:/# exit
root@14asdfj8ad83:/# Ctl + P + Q
```

# [docker commit](00_docker_command/10_docker_commit.md)
```{bash}
$ docker commit 42ff601ded9a ubuntu:14.04-python2.7
```

# [BusyBox : The Swiss Army Knife of Embedded Linux](00_docker_command/11_BusyBox_on_docker.md)
```{bash}
$ docker create -v /var/lib/postgresql/data --name postgres9.3.6-data busybox
```

# [docker volumn](00_docker_command/12_docker_volumn.md)
```{bash}
$ docker create -v `pwd`/testFolder:/tmp/testFolder --name dataContainer busybox
$ docker run -it --name localContainer -d --volumes-from dataContainer busybox:latest sh
```

# [gitlab_on_docker](00_docker_command/13_gitlab_ce_on_docker.md)
```{bash}
$ docker start gitlab
http://localhost
$ docker stop gitlab
```

# [docker inspect](00_docker_command/14_docker_inspect.md)
```{bash}
$ docker inspect --format "{{ json .Mounts }}" gitlab | python -m json.tool
```

# [docker copy](00_docker_command/15_docker_cp.md)
```{bash}
$ docker cp scala-2.12.1.deb ubuntu14.04:/
```

# [docker build](00_docker_command/16_docker_build.md)
```{bash}
$ docker build -t image:tag -f Dockerfile .
$ docker images
```
