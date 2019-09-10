# download the basic ubuntu 14.04 image
```
$ docker images
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE

$ docker pull ubuntu:14.04
14.04: Pulling from library/ubuntu
Digest: sha256:881befbe6f54c1e85029fe3a11554342bf765a0849600ecb8fa2f922798b4925
Status: Downloaded newer image for ubuntu:14.04

$ docker images
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
ubuntu                         14.04               3f755ca42730        12 days ago         188 MB
```
