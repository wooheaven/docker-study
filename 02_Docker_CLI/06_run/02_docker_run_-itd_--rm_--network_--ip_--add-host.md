```
$ docker run -itd --rm \
--name namenode \
--network mynet \
--ip 172.20.0.2 \
--add-host=namenode:172.20.0.2 \
--add-host=datanode1:172.20.0.3 \
--add-host=datanode2:172.20.0.4 \
ubuntu:16.04_4th_spark_yarn
227df1cff930e17420b7958b65b117b10bb6227dea874707851490597f4d5caa

$ docker run -itd --rm \
--name datanode1 \
--network mynet \
--ip 172.20.0.3 \
--add-host=namenode:172.20.0.2 \
--add-host=datanode1:172.20.0.3 \
--add-host=datanode2:172.20.0.4 \
ubuntu:16.04_4th_spark_yarn
44c15412317b30cbafe869ef0ac6adfa48889eb36fbb7d91e3603b81b085c422

$ docker run -itd --rm \
--name datanode2 \
--network mynet \
--ip 172.20.0.4 \
--add-host=namenode:172.20.0.2 \
--add-host=datanode1:172.20.0.3 \
--add-host=datanode2:172.20.0.4 \
ubuntu:16.04_4th_spark_yarn

$ docker exec namenode ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:ac:14:00:02  
          inet addr:172.20.0.2  Bcast:172.20.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15452 (15.4 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:260406 (260.4 KB)  TX bytes:260406 (260.4 KB)

$ docker exec namenode route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         172.20.0.1      0.0.0.0         UG    0      0        0 eth0
172.20.0.0      *               255.255.0.0     U     0      0        0 eth0

$ docker exec datanode1 ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:ac:14:00:03  
          inet addr:172.20.0.3  Bcast:172.20.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8432 (8.4 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:249986 (249.9 KB)  TX bytes:249986 (249.9 KB)

$ docker exec datanode1 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         172.20.0.1      0.0.0.0         UG    0      0        0 eth0
172.20.0.0      *               255.255.0.0     U     0      0        0 eth0

$ docker exec namenode ping -c 3 datanode1
PING datanode1 (172.20.0.3) 56(84) bytes of data.
64 bytes from datanode1 (172.20.0.3): icmp_seq=1 ttl=64 time=0.053 ms
64 bytes from datanode1 (172.20.0.3): icmp_seq=2 ttl=64 time=0.098 ms
64 bytes from datanode1 (172.20.0.3): icmp_seq=3 ttl=64 time=0.100 ms

--- datanode1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2028ms
rtt min/avg/max/mdev = 0.053/0.083/0.100/0.024 ms

$ docker exec namenode ping -c 3 datanode2
PING datanode2 (172.20.0.4) 56(84) bytes of data.
64 bytes from datanode2 (172.20.0.4): icmp_seq=1 ttl=64 time=0.068 ms
64 bytes from datanode2 (172.20.0.4): icmp_seq=2 ttl=64 time=0.102 ms
64 bytes from datanode2 (172.20.0.4): icmp_seq=3 ttl=64 time=0.100 ms

--- datanode2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2026ms
rtt min/avg/max/mdev = 0.068/0.090/0.102/0.015 ms
```
