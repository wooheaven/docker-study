# check local docker container process
```
# check current container process
docker ps
 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
42ff601ded9a        ubuntu:14.04        "/bin/bash"         5 minutes ago       Up 5 minutes                            kickass_perlman

# check all container process
docker ps -a

CONTAINER ID        IMAGE                                       COMMAND             CREATED             STATUS                    PORTS               NAMES
42ff601ded9a        ubuntu:14.04                                "/bin/bash"         19 minutes ago      Up 19 minutes                                 kickass_perlman
d3db45184ba2        imcomking/bi_deeplearning                   "/bin/bash"         4 weeks ago         Exited (0) 2 weeks ago                        agitated_torvalds
3689e09f6394        gcr.io/tensorflow/tensorflow:latest-devel   "/bin/bash"         11 weeks ago        Exited (0) 11 weeks ago                       tensorflow
```
