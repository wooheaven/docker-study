# check docker container's port
```
docker ps
CONTAINER ID        IMAGE                    COMMAND             CREATED             STATUS              PORTS                      NAMES
572d7d576089        ubuntu:14.04-python2.7   "/bin/bash"         40 seconds ago      Up 39 seconds       127.0.0.1:9999->9999/tcp   compassionate_bell

docker port 572d7d576089
9999/tcp -> 127.0.0.1:9999
```
