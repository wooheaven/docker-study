# run docker container on local
```{bash}
docker images
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
ubuntu                         14.04-python2.7     b3509fe48f72        47 hours ago        2.505 GB

docker run -it -p 127.0.0.1:9999:9999 -v /Users/rwoo/2_Workspace/17_Python_workspace/Python2.7-Study:/home/python_workspace --name="py27study" ubuntu:14.04-python2.7 /bin/bash

root@11454d991235:/# ll /home/
total 8
drwxr-xr-x  3 root root 4096 Jan 10 14:06 ./
drwxr-xr-x 41 root root 4096 Jan 10 14:06 ../
drwxr-xr-x  5 root root  170 Dec 31 16:17 python_workspace/

root@11454d991235:/# Ctl + P + Q

docker ps
CONTAINER ID        IMAGE                    COMMAND             CREATED             STATUS              PORTS                      NAMES
11454d991235        ubuntu:14.04-python2.7   "/bin/bash"         10 seconds ago      Up 7 seconds        127.0.0.1:9999->9999/tcp   py27study
```
