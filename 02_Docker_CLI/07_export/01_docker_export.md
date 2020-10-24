# docker export
```
$ docker ps -a
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS                     PORTS               NAMES
67cfd5f121eb        ubuntu:18.04_5th_jupyter_pyspark   "/bin/bash"              2 months ago        Exited (0) 5 days ago                          spark_yarn_jupyter_pyspark

$ docker export spark_yarn_jupyter_pyspark > spark.tar
```

# docker import
```
$ docker import spark.tar spark:test
sha256:2364b7685c7b0325f454a6d969bfb996202630f80990970cea3c5b59f83ffedd

$ docker images 
REPOSITORY               TAG                         IMAGE ID            CREATED             SIZE
spark                    test                        2364b7685c7b        10 seconds ago      2.45GB
```
