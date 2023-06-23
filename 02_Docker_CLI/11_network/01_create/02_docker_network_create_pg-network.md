# create network
```
$ docker network create postgres-network
```

# use network
```
$ docker run -itd \
-e "PGADMIN_DEFAULT_EMAIL=wooheaven79@gmail.com" \
-e "PGADMIN_DEFAULT_PASSWORD=123qwe" \
-p 65433:80 \
--name pgadmin4 \
--network postgres-network \
dpage/pgadmin4
$ docker network connect postgres-network pg15.1-Container
$ docker network connect postgres-network pg-DBContainer
```

# inspect network
```
$ docker network inspect postgres-network 
[
    {
        "Name": "postgres-network",
        "Id": "e981055fec78a84af762cfde576310417a31ad4dcb5d6025f9d5644aa4f3b11c",
        "Created": "2023-06-20T06:59:54.188380388+09:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.19.0.0/16",
                    "Gateway": "172.19.0.1"
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
        "Containers": {
            "173bfaf38b23e8e516f69fbf6ba6e31555e7f8ed4e147154605339f11eb2e4d4": {
                "Name": "pg15.1-Container",
                "EndpointID": "706064b3b242540d201af9d24a247efc38a2cde3c4003e29b236b4790dda0c20",
                "MacAddress": "02:42:ac:13:00:03",
                "IPv4Address": "172.19.0.3/16",
                "IPv6Address": ""
            },
            "24fd9dc2ee7caa348d626044dfb7ce5edba9b7c5d6de1c10e1c1f534148210cf": {
                "Name": "pg-DBContainer",
                "EndpointID": "9568b1946b652f8a639406d53808ab4a78928df2da683f3c47e33d9071a8d0d9",
                "MacAddress": "02:42:ac:13:00:02",
                "IPv4Address": "172.19.0.2/16",
                "IPv6Address": ""
            },
            "61874105fdcebe9d7fb3e1baca0fa9f2fe478c07d356461cfa00b3612426d852": {
                "Name": "pgadmin4",
                "EndpointID": "18a13ce7f6542f9833a31c093b1334f2ea40feb475d06fee42d0a52a6a59649a",
                "MacAddress": "02:42:ac:13:00:04",
                "IPv4Address": "172.19.0.4/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]
```

# ping
```
$ docker ps
CONTAINER ID   IMAGE                COMMAND                  CREATED        STATUS             PORTS                                              NAMES
61874105fdce   dpage/pgadmin4       "/entrypoint.sh"         16 hours ago   Up About an hour   443/tcp, 0.0.0.0:65433->80/tcp, :::65433->80/tcp   pgadmin4
173bfaf38b23   postgres:15.1        "docker-entrypoint.s…"   6 months ago   Up 2 hours         0.0.0.0:55432->5432/tcp, :::55432->5432/tcp        pg15.1-Container
24fd9dc2ee7c   postgres:13-alpine   "docker-entrypoint.s…"   2 years ago    Up 2 hours         0.0.0.0:65432->5432/tcp, :::65432->5432/tcp        pg-DBContainer

$ docker exec pgadmin4 ping pg15.1-Container
PING pg15.1-Container (172.19.0.3): 56 data bytes
64 bytes from 172.19.0.3: seq=0 ttl=42 time=0.082 ms
64 bytes from 172.19.0.3: seq=1 ttl=42 time=0.162 ms
64 bytes from 172.19.0.3: seq=2 ttl=42 time=0.157 ms
64 bytes from 172.19.0.3: seq=3 ttl=42 time=0.157 ms
64 bytes from 172.19.0.3: seq=4 ttl=42 time=0.183 ms
^C

$ docker exec pgadmin4 ping 172.19.0.2 -c 5
PING 172.19.0.2 (172.19.0.2): 56 data bytes
64 bytes from 172.19.0.2: seq=0 ttl=42 time=0.073 ms
64 bytes from 172.19.0.2: seq=1 ttl=42 time=0.168 ms
64 bytes from 172.19.0.2: seq=2 ttl=42 time=0.160 ms
64 bytes from 172.19.0.2: seq=3 ttl=42 time=0.161 ms
64 bytes from 172.19.0.2: seq=4 ttl=42 time=0.161 ms

--- 172.19.0.2 ping statistics ---
5 packets transmitted, 5 packets received, 0% packet loss
round-trip min/avg/max = 0.073/0.144/0.168 ms

$ docker exec pg15.1-Container ping 172.19.0.2 -c 5
PING 172.19.0.2 (172.19.0.2) 56(84) bytes of data.
64 bytes from 172.19.0.2: icmp_seq=1 ttl=64 time=0.095 ms
64 bytes from 172.19.0.2: icmp_seq=2 ttl=64 time=0.101 ms
64 bytes from 172.19.0.2: icmp_seq=3 ttl=64 time=0.047 ms
64 bytes from 172.19.0.2: icmp_seq=4 ttl=64 time=0.104 ms
64 bytes from 172.19.0.2: icmp_seq=5 ttl=64 time=0.096 ms

--- 172.19.0.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4100ms
rtt min/avg/max/mdev = 0.047/0.088/0.104/0.021 ms
```
