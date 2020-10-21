# docker network bridge
```
docker daemon을 실행하면 먼저 docker0 라는 bridge가 생성된다. 
컨테이너를 생성하게 되면, 각 컨테이너마다 고유한 network namespace 영역이 하나씩 생성되며, 
이때 docker0 bridge에 container의 인터페이스들이 하나씩 binding 되는 구조이다.

docker0 is a network interface on Host
vethc2fa539@if251 is a interface which binding to the bridge docker0
# ref : https://bluese05.tistory.com/15
```

# docker run with [docker network bridge]
```
$ docker run -it --cpus="4" \
-p 8088:8088 \
-p 18080:18080 \
-p 8042:8042 \
--name spark ubuntu:16.04_4th_spark_yarn

$ docker run -it --cpus="4" \
-p 8088:8088 \
-p 18080:18080 \
-p 8042:8042 \
--net docker0 \
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
252: vethc2fa539@if251: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP mode DEFAULT group default 
    link/ether 0e:7f:26:b4:fb:5a brd ff:ff:ff:ff:ff:ff link-netnsid 0

$ ifconfig 
docker0   Link encap:Ethernet  HWaddr 02:42:ba:50:72:30  
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          inet6 addr: fe80::42:baff:fe50:7230/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:148472 (148.4 KB)  TX bytes:16518464 (16.5 MB)

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

vethc2fa539 Link encap:Ethernet  HWaddr 0e:7f:26:b4:fb:5a  
          inet6 addr: fe80::c7f:26ff:feb4:fb5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:172658 (172.6 KB)  TX bytes:16397291 (16.3 MB)

$ docker exec spark ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 02:42:ac:11:00:02  
          inet addr:172.17.0.2  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16396439 (16.3 MB)  TX bytes:172658 (172.6 KB)

$ docker exec spark route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         172.17.0.1      0.0.0.0         UG    0      0        0 eth0
172.17.0.0      *               255.255.0.0     U     0      0        0 eth0

$ docker network inspect bridge 
[
    {
        "Name": "bridge",
        "Id": "e70081f66a74b508a7e6c982da781db0daca619d59882737ce9a340190f06fda",
        "Created": "2019-09-09T18:33:46.058585925+09:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.17.0.0/16",
                    "Gateway": "172.17.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {},
        "Options": {
            "com.docker.network.bridge.default_bridge": "true",
            "com.docker.network.bridge.enable_icc": "true",
            "com.docker.network.bridge.enable_ip_masquerade": "true",
            "com.docker.network.bridge.host_binding_ipv4": "0.0.0.0",
            "com.docker.network.bridge.name": "docker0",
            "com.docker.network.driver.mtu": "1500"
        },
        "Labels": {}
    }
]
```
