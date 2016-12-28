# stop docker container and exit docker container
```
docker ps
 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
42ff601ded9a        ubuntu:14.04        "/bin/bash"         5 minutes ago       Up 5 minutes                            kickass_perlman

docker attach 42ff601ded9a

root@42ff601ded9a:/# exit
exit

docker ps
 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```
