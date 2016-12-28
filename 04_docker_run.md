# run docker container on local
```
docker images

REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
ubuntu                         14.04               3f755ca42730        12 days ago         188 MB
tensorflow                     ch2                 0b1caa86248b        11 weeks ago        2.776 GB
gcr.io/tensorflow/tensorflow   latest-devel        ef3b8aa4d0c3        3 months ago        2.775 GB
imcomking/bi_deeplearning      latest              471a9be7cc90        3 months ago        7.183 GB

# connect container as /bin/bash
docker run -i -t ubuntu:14.04 /bin/bash
root@42ff601ded9a:/#

# disconnect container without stop container
root@42ff601ded9a:/# Ctrl + p + q

# check container process
docker ps
 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
42ff601ded9a        ubuntu:14.04        "/bin/bash"         5 minutes ago       Up 5 minutes                            kickass_perlman
```
