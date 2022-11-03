# [BusyBox : The Swiss Army Knife of Embedded Linux]
```{bash}
$ docker pull busybox
$ docker pull postgres:9.3.6
$ docker images 
REPOSITORY              TAG                      IMAGE ID            CREATED             SIZE
busybox                 latest                   19485c79a9bb        2 weeks ago         1.22MB
postgres                9.3.6                    e66064e079dd        4 years ago         213MB

$ docker create \
-v `pwd`/var/lib/postgresql/data:/var/lib/postgresql/data \
--name postgresql9.3.6-DataContainer busybox:latest

$ docker run \
-d \
-p 65432:5432 \
-e POSTGRES_PASSWORD=123qwe \
--volumes-from postgresql9.3.6-DataContainer \
--name postgresql9.3.6-Container postgres:9.3.6
```
