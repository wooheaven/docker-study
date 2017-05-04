# start a container
```
docker ps -a

CONTAINER ID        IMAGE                                       COMMAND             CREATED             STATUS                      PORTS               NAMES
42ff601ded9a        ubuntu:14.04                                "/bin/bash"         6 hours ago         Exited (0) 17 minutes ago                       kickass_perlman
d3db45184ba2        imcomking/bi_deeplearning                   "/bin/bash"         4 weeks ago         Exited (0) 2 weeks ago                          agitated_torvalds
3689e09f6394        gcr.io/tensorflow/tensorflow:latest-devel   "/bin/bash"         12 weeks ago        Exited (0) 12 weeks ago                         tensorflow

docker start 42ff601ded9a
42ff601ded9a

docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
42ff601ded9a        ubuntu:14.04        "/bin/bash"         6 hours ago         Up About a minute                       kickass_perlman
```
