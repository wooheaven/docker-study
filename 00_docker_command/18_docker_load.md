# docker load from image file
```
docker load -i cpuminer-multi.tar
```

# check docker images
```
docker images
```

# docker tag image
```
docker tag 310 cpuminer-multi:latest
```

# check docker images
```
docker images
```

# real log
```
$ docker load -i cpuminer-multi.tar
3027cf2efece: Loading layer [==================================================>]  21.21MB/21.21MB
4e0402ee99b0: Loading layer [==================================================>]  231.7MB/231.7MB
9b14c1ec550c: Loading layer [==================================================>]  75.89MB/75.89MB
9383c1d27b9b: Loading layer [==================================================>]  9.845MB/9.845MB
Loaded image ID: sha256:3103659678ba5376f7a18e8d76538a915d66b22c512f16741ed5aee59061fd19

$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
<none>              <none>              3103659678ba        16 hours ago        551MB
ubuntu              14.04               dc4491992653        2 weeks ago         222MB

$ docker tag 310 cpuminer-multi:latest

$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
cpuminer-multi      latest              3103659678ba        16 hours ago        551MB
ubuntu              14.04               dc4491992653        2 weeks ago         222MB
```
