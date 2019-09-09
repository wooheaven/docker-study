# before 
```
$ docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
d778d86d2c53        bridge              bridge              local
29cb07a4b68b        host                host                local
18fae3e4fab0        none                null                local

$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 54:ee:75:8f:3a:89 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 08:d4:0c:9e:07:d7 brd ff:ff:ff:ff:ff:ff
4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether 02:42:6d:bb:64:cd brd ff:ff:ff:ff:ff:ff

$ ifconfig 
docker0   Link encap:Ethernet  HWaddr 02:42:6d:bb:64:cd  
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

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
          RX packets:5004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5004 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:470933 (470.9 KB)  TX bytes:470933 (470.9 KB)

wlp2s0    Link encap:Ethernet  HWaddr 08:d4:0c:9e:07:d7  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b767:b6bc:c756:411a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:159298863 (159.2 MB)  TX bytes:13325245 (13.3 MB)

$ docker network inspect bridge
[
    {
        "Name": "bridge",
        "Id": "d778d86d2c5389166620d34401918379002c4adb0fa5c7ac6acf891937343509",
        "Created": "2019-09-09T08:00:34.728586411+09:00",
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

# after
```
$ docker network create \
> --driver bridge \
> --subnet 172.20.0.0/16 \
> --ip-range 172.20.0.0/24 \
> --gateway 172.20.0.1 \
> mynet
9bc3af96b422c8c6857bb2017c1bc1f4bb93f6e4907d19314f577e07df5b0b43

$ ip link 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 54:ee:75:8f:3a:89 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 08:d4:0c:9e:07:d7 brd ff:ff:ff:ff:ff:ff
4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether 02:42:6d:bb:64:cd brd ff:ff:ff:ff:ff:ff
13: br-9bc3af96b422: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether 02:42:60:6b:cd:5d brd ff:ff:ff:ff:ff:ff

$ ifconfig 
br-9bc3af96b422 Link encap:Ethernet  HWaddr 02:42:60:6b:cd:5d  
          inet addr:172.20.0.1  Bcast:172.20.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

docker0   Link encap:Ethernet  HWaddr 02:42:6d:bb:64:cd  
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

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
          RX packets:8870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:828129 (828.1 KB)  TX bytes:828129 (828.1 KB)

wlp2s0    Link encap:Ethernet  HWaddr 08:d4:0c:9e:07:d7  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b767:b6bc:c756:411a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:262368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:294450119 (294.4 MB)  TX bytes:20988156 (20.9 MB)

$ docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
7bbd5252cd70        bridge              bridge              local
29cb07a4b68b        host                host                local
9bc3af96b422        mynet               bridge              local
18fae3e4fab0        none                null                local

$ docker network inspect mynet 
[
    {
        "Name": "mynet",
        "Id": "9bc3af96b422c8c6857bb2017c1bc1f4bb93f6e4907d19314f577e07df5b0b43",
        "Created": "2019-09-09T14:42:02.54365251+09:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.20.0.0/16",
                    "IPRange": "172.20.0.0/24",
                    "Gateway": "172.20.0.1"
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
        "Options": {},
        "Labels": {}
    }
]
```
