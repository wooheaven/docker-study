```
# --interactive , -i : Keep STDIN open even if not attached
# --tty , -t         : Allocate a pseudo-TTY

$ docker run -it --name test ubuntu:16.04 bash
root@4be9db430c30:/# ps -aef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  1 11:27 pts/0    00:00:00 bash
root        10     1  0 11:28 pts/0    00:00:00 ps -aef

root@4be9db430c30:/# exit
exit

$ docker ps -a
CONTAINER ID      IMAGE             COMMAND         CREATED           STATUS                     PORTS         NAMES
4be9db430c30      ubuntu:16.04      "bash"          32 seconds ago    Exited (0) 2 seconds ago                 test
```
