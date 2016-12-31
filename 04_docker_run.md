# run docker container on local
```
docker images
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
ubuntu                         14.04-python2.7     b3509fe48f72        47 hours ago        2.505 GB

docker run -it -p 127.0.0.1:9999:9999 ubuntu:14.04-python2.7 /bin/bash
root@572d7d576089:/#

root@572d7d576089:/# ps -a
# run docker container on local
  PID TTY          TIME CMD
   16 ?        00:00:00 ps
root@572d7d576089:/# Ctrl + p + q

docker ps
CONTAINER ID        IMAGE                    COMMAND             CREATED             STATUS              PORTS                      NAMES
572d7d576089        ubuntu:14.04-python2.7   "/bin/bash"         40 seconds ago      Up 39 seconds       127.0.0.1:9999->9999/tcp   compassionate_bell

docker port 572d7d576089
9999/tcp -> 127.0.0.1:9999
```
