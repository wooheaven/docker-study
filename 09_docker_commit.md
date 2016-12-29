# save container as a new image or existing image name
```
docker ps -a
CONTAINER ID        IMAGE                                       COMMAND             CREATED             STATUS                     PORTS               NAMES
42ff601ded9a        ubuntu:14.04                                "/bin/bash"         31 hours ago        Exited (0) 3 minutes ago                       kickass_perlman
d3db45184ba2        imcomking/bi_deeplearning                   "/bin/bash"         4 weeks ago         Exited (0) 3 weeks ago                         agitated_torvalds
3689e09f6394        gcr.io/tensorflow/tensorflow:latest-devel   "/bin/bash"         12 weeks ago        Exited (0) 12 weeks ago                        tensorflow

docker commit 42ff601ded9a ubuntu:14.04-python2.7
sha256:b3509fe48f72e883734034bb27111ae66a5e93bd32c30c0faa4d8933c8237645

docker images
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
ubuntu                         14.04-python2.7     b3509fe48f72        34 seconds ago      2.505 GB
ubuntu                         14.04               3f755ca42730        13 days ago         188 MB
tensorflow                     ch2                 0b1caa86248b        12 weeks ago        2.776 GB
gcr.io/tensorflow/tensorflow   latest-devel        ef3b8aa4d0c3        3 months ago        2.775 GB
imcomking/bi_deeplearning      latest              471a9be7cc90        3 months ago        7.183 GB
```
