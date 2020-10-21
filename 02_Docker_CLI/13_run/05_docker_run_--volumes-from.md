# [docker volumn](12_docker_volumn.md)
```{bash}
$ mkdir -p ./testFolder

$ # Bind mount a volumn 
$ docker create -v `pwd`/testFolder:/tmp/testFolder --name dataContainer busybox

$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS             PORTS               NAMES
44a1f143ec02        busybox             "sh"                19 minutes ago      Created            dataContainer

$ # Mount volumes from the specified container(s)
$ docker run -it --name localContainer -d --volumes-from dataContainer busybox:latest sh
db35027a68ef4968199cb42b1f24a2383937f46424e4397a4fabe0d863d9b31f

$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS             PORTS               NAMES
db35027a68ef        busybox:latest      "sh"                5 seconds ago       Up 3 seconds                           localContainer

$ docker attach db35027a68ef

/ # cd tmp/testFolder/

/tmp/testFolder # touch sample

/tmp/testFolder # exit

$ docker ps 
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

$ ls -als testFolder/
total 8
4 drwxrwxr-x 2 rwoo rwoo 4096  3월 13 04:25 .
4 drwxrwxr-x 4 rwoo rwoo 4096  3월 13 03:50 ..
0 -rw-r--r-- 1 root root    0  3월 13 04:25 sample
```
