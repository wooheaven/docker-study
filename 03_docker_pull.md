# download the basic ubuntu 14.04 image
```
docker images

REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
tensorflow                     ch2                 0b1caa86248b        11 weeks ago        2.776 GB
gcr.io/tensorflow/tensorflow   latest-devel        ef3b8aa4d0c3        3 months ago        2.775 GB
imcomking/bi_deeplearning      latest              471a9be7cc90        3 months ago        7.183 GB

docker pull ubuntu:14.04

14.04: Pulling from library/ubuntu
16da43b30d89: Pulling fs layer
1840843dafed: Pulling fs layer
91246eb75b7d: Pulling fs layer
7faa681b41d7: Pulling fs layer
97b84c64d426: Pulling fs layer
97b84c64d426: Waiting
7faa681b41d7: Waiting
1840843dafed: Download complete
91246eb75b7d: Download complete
97b84c64d426: Verifying Checksum
97b84c64d426: Download complete
7faa681b41d7: Verifying Checksum
7faa681b41d7: Download complete
16da43b30d89: Verifying Checksum
16da43b30d89: Download complete
16da43b30d89: Pull complete
1840843dafed: Pull complete
91246eb75b7d: Pull complete
7faa681b41d7: Pull complete
97b84c64d426: Pull complete
Digest: sha256:881befbe6f54c1e85029fe3a11554342bf765a0849600ecb8fa2f922798b4925
Status: Downloaded newer image for ubuntu:14.04

docker images

REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
ubuntu                         14.04               3f755ca42730        12 days ago         188 MB
tensorflow                     ch2                 0b1caa86248b        11 weeks ago        2.776 GB
gcr.io/tensorflow/tensorflow   latest-devel        ef3b8aa4d0c3        3 months ago        2.775 GB
imcomking/bi_deeplearning      latest              471a9be7cc90        3 months ago        7.183 GB
```
