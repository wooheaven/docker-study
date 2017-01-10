# stop docker container and exit docker container
```{bash}
docker ps
 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
42ff601ded9a        ubuntu:14.04        "/bin/bash"         5 minutes ago       Up 5 minutes                            kickass_perlman

docker attach 42ff601ded9a

root@42ff601ded9a:/# exit
exit

docker ps
 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

# exit docker container without stop docker container
```{bash}
docker start 7a59264be34e
7a59264be34e

docker attach 7a59264be34e
root@7a59264be34e:/# Ctl + P + Q

docker ps
CONTAINER ID        IMAGE                    COMMAND             CREATED             STATUS              PORTS                      NAMES
7a59264be34e        ubuntu:14.04-python2.7   "/bin/bash"         9 days ago          Up 30 seconds       127.0.0.1:8888->8888/tcp   cranky_booth
```
