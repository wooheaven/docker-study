# check docker container
```
docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

# check docker images
```
docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
cpuminer-multi      latest              3103659678ba        14 hours ago        551MB
ubuntu              14.04               dc4491992653        2 weeks ago         222MB
```

# docker save image to tar
```
docker save 3103659678ba > cpuminer-multi.tar
```

# scp image file
```
scp cpuminer-multi.tar test@192.168.3.40:`pwd`/
cpuminer-multi.tar                                     100%  326MB  51.4MB/s   00:cpuminer- 100%  543MB  41.8MB/s   00:13
```

# docker load tar to image
```
docker load -i cpuminer-multi.tar
```
