# docker network container
```
container 방식으로 컨테이너를 생성하면, 기존에 존재하는 다른 컨테이너의 network 환경을 공유하게 된다. 
```

# docker run with [docker network container]
```
$ docker run -it --cpus="4" \
> -p 8088:8088 \
> -p 18080:18080 \
> -p 8042:8042 \
> --name spark ubuntu:16.04_4th_spark_yarn

$ docker run -it --cpus="4" \
> --net=container:spark \
> --name spark2 ubuntu:16.04_4th_spark_yarn

$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 54:ee:75:8f:3a:89 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 08:d4:0c:9e:07:d7 brd ff:ff:ff:ff:ff:ff
4: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default 
    link/ether 02:42:ba:50:72:30 brd ff:ff:ff:ff:ff:ff
334: veth81bb979@if333: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP mode DEFAULT group default 
    link/ether d6:a4:f9:7d:aa:c4 brd ff:ff:ff:ff:ff:ff link-netnsid 0

$ ifconfig 
docker0   Link encap:Ethernet  HWaddr 02:42:ba:50:72:30  
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          inet6 addr: fe80::42:baff:fe50:7230/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:915320 (915.3 KB)  TX bytes:68253304 (68.2 MB)

enp3s0    Link encap:Ethernet  HWaddr 54:ee:75:8f:3a:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:11038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2373886 (2.3 MB)  TX bytes:2373886 (2.3 MB)

veth81bb979 Link encap:Ethernet  HWaddr d6:a4:f9:7d:aa:c4  
          inet6 addr: fe80::d4a4:f9ff:fe7d:aac4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1730 (1.7 KB)  TX bytes:12357 (12.3 KB)

wlp2s0    Link encap:Ethernet  HWaddr 08:d4:0c:9e:07:d7  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b767:b6bc:c756:411a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:169144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:214207670 (214.2 MB)  TX bytes:9876940 (9.8 MB)

$ docker exec spark ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:ac:11:00:02  
          inet addr:172.17.0.2  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12357 (12.3 KB)  TX bytes:1730 (1.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2467543 (2.4 MB)  TX bytes:2467543 (2.4 MB)

$ docker exec spark route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         172.17.0.1      0.0.0.0         UG    0      0        0 eth0
172.17.0.0      *               255.255.0.0     U     0      0        0 eth0

$ docker exec spark2 ifconfig
eth0      Link encap:Ethernet  HWaddr 02:42:ac:11:00:02  
          inet addr:172.17.0.2  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13163 (13.1 KB)  TX bytes:1897 (1.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2481544 (2.4 MB)  TX bytes:2481544 (2.4 MB)

$ docker exec spark2 route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         172.17.0.1      0.0.0.0         UG    0      0        0 eth0
172.17.0.0      *               255.255.0.0     U     0      0        0 eth0
```
