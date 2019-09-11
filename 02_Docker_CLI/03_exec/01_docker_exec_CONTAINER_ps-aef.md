# docker exec CONTAINER ps -aef
```{bash}
$ docker exec -it test1 ps -aef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Jun18 pts/0    00:00:00 /bin/bash
root      3831     0  0 02:12 pts/1    00:00:00 ps -eaf
```
