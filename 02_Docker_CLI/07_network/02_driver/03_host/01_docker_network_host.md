# docker network host
```
host 방식으로 컨테이너를 생성하면, 컨테이너가 독립적인 네트워크 영역을 갖지 않고 host와 네트워크를 함께 사용하게 된다. 
```

# docker run with [docker network host]
```
$ docker run -it --cpus="4" \
-p 8088:8088 \
-p 18080:18080 \
-p 8042:8042 \
--net=host \
--name spark ubuntu:16.04_4th_spark_yarn

$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 54:ee:75:8f:3a:89 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 08:d4:0c:9e:07:d7 brd ff:ff:ff:ff:ff:ff
4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether 02:42:ba:50:72:30 brd ff:ff:ff:ff:ff:ff

$ ifconfig 
docker0   Link encap:Ethernet  HWaddr 02:42:ba:50:72:30  
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          inet6 addr: fe80::42:baff:fe50:7230/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:149247 (149.2 KB)  TX bytes:16534195 (16.5 MB)

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
          RX packets:5481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1651324 (1.6 MB)  TX bytes:1651324 (1.6 MB)

wlp2s0    Link encap:Ethernet  HWaddr 08:d4:0c:9e:07:d7  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b767:b6bc:c756:411a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115128624 (115.1 MB)  TX bytes:5043688 (5.0 MB)

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
link-local      *               255.255.0.0     U     1000   0        0 wlp2s0
172.17.0.0      *               255.255.0.0     U     0      0        0 docker0
172.20.0.0      *               255.255.0.0     U     0      0        0 br-9bc3af96b422
192.168.0.0     *               255.255.255.0   U     600    0        0 wlp2s0

$ docker exec spark ifconfig
docker0   Link encap:Ethernet  HWaddr 02:42:ba:50:72:30  
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          inet6 addr: fe80::42:baff:fe50:7230/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:149247 (149.2 KB)  TX bytes:16534195 (16.5 MB)

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
          RX packets:5481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1651324 (1.6 MB)  TX bytes:1651324 (1.6 MB)

wlp2s0    Link encap:Ethernet  HWaddr 08:d4:0c:9e:07:d7  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b767:b6bc:c756:411a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115128624 (115.1 MB)  TX bytes:5043688 (5.0 MB)

$ docker exec spark route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
link-local      *               255.255.0.0     U     1000   0        0 docker0
172.17.0.0      *               255.255.0.0     U     0      0        0 docker0
192.168.0.0     *               255.255.255.0   U     600    0        0 wlp2s0

$ docker network inspect host
[
    {
        "Name": "host",
        "Id": "29cb07a4b68be556a6dbc6ddf098d4fe4a571c21be158a802d64390944f73374",
        "Created": "2019-06-08T23:27:42.849777666+09:00",
        "Scope": "local",
        "Driver": "host",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": []
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {},
        "Labels": {}
    }
]
```
