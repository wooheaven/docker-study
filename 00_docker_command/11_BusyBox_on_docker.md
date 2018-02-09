# [BusyBox : The Swiss Army Knife of Embedded Linux]
```{bash}
$ docker search busybox
NAME                            DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
busybox                         Busybox base image.                             951       [OK]       
progrium/busybox                                                                65                   [OK]
radial/busyboxplus              Full-chain, Internet enabled, busybox made...   11                   [OK]
container4armhf/armhf-busybox   Automated build of Busybox for armhf devic...   6                    [OK]
odise/busybox-python                                                            4                    [OK]
ofayau/busybox-jvm              Prepare busybox to install a 32 bits JVM.       2                    [OK]
multiarch/busybox               multiarch ports of ubuntu-debootstrap           2                    [OK]
azukiapp/busybox                This image is meant to be used as the base...   2                    [OK]
sequenceiq/busybox                                                              2                    [OK]
getblank/busybox                Docker container busybox for Blank              1                    [OK]
odise/busybox-curl                                                              1                    [OK]
elektritter/busybox-teamspeak   Leightweight teamspeak3 container based on...   1                    [OK]
ofayau/busybox-libc32           Busybox with 32 bits (and 64 bits) libs         1                    [OK]
skomma/busybox-data             Docker image suitable for data volume cont...   1                    [OK]
ddn0/busybox                    fork of official busybox                        0                    [OK]
jahroots/busybox                Busybox containers                              0                    [OK]
cucy/busybox                    aouto  build busybox                            0                    [OK]
sdurrheimer/prom-busybox        Moved to https://hub.docker.com/r/prom/bus...   0                    [OK]
padcom/busybox-java             Oracle Java on BusyBox                          0                    [OK]
ggtools/busybox-ubuntu          Busybox ubuntu version with extra goodies       0                    [OK]
jiangshouzhuang/busybox         busybox                                         0                    [OK]
futurenda/busybox               Mini busybox                                    0                    [OK]
prom/busybox                    Prometheus Busybox Docker base images           0                    [OK]
freenas/busybox                 Simple Busybox interactive Linux container      0                    [OK]
hongtao12310/busybox            for busybox image based on the gcr.io/goog...   0                    [OK]

$ docker pull busybox
Using default tag: latest
latest: Pulling from library/busybox
7520415ce762: Pull complete 
Digest: sha256:32f093055929dbc23dec4d03e09dfe971f5973a9ca5cf059cbfb644c206aa83f
Status: Downloaded newer image for busybox:latest

$ docker images 
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
busybox                        latest              00f017a8c2a6        2 days ago          1.11 MB
microsoft/azure-cli            latest              bccdaa9f5de0        2 weeks ago         540.1 MB
tensorflow                     chapter3            4799641d3e61        5 months ago        3.072 GB
gcr.io/tensorflow/tensorflow   latest-devel        ef3b8aa4d0c3        5 months ago        2.775 GB

$ docker create -v /var/lib/postgresql/data --name postgres9.3.6-data busybox
```
