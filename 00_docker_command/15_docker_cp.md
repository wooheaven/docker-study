# Docker cp host to container
```{bash}
rwoo@rwoo-A610:~/Downloads$ ll scala-2.12.1.deb 
-rw------- 1 rwoo rwoo 151677438 12월  5 20:21 scala-2.12.1.deb

rwoo@rwoo-A610:~/Downloads$ docker cp scala-2.12.1.deb ubuntu14.04:/

rwoo@rwoo-A610:~/Downloads$ docker attach ubuntu14.04

root@f242ad934e35:/# ll scala-2.12.1.deb 
-rw------- 1 root root 151677438 May 20 17:22 scala-2.12.1.deb
```
