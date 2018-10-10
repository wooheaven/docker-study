# docker tag for rename docker image's [REPOSITORY, TAG]
```{bash}
ubuntu@ubuntu:~/Documents/docker/02_test$ docker pull timonmat/xmr-stak-cpu
Using default tag: latest
latest: Pulling from timonmat/xmr-stak-cpu
1eae7a7426b0: Pull complete
129a1299f872: Pull complete
3d68eb5664b7: Pull complete
b0c5e4de86a7: Pull complete
6f21242f4b1c: Pull complete
Digest: sha256:cd5357198ef52fbdb16a1db04f59661316bb6533782fda922a94f651bff92da1
Status: Downloaded newer image for timonmat/xmr-stak-cpu:latest

ubuntu@ubuntu:~/Documents/docker/02_test$ docker images
REPOSITORY              TAG                     IMAGE ID            CREATED             SIZE
timonmat/xmr-stak-cpu   latest                  a1286fc11cef        6 months ago        65.2MB

ubuntu@ubuntu:~/Documents/docker/02_test$ docker tag a1286fc11cef test/test:latest

ubuntu@ubuntu:~/Documents/docker/02_test$ docker images
REPOSITORY              TAG                     IMAGE ID            CREATED             SIZE
test/test               latest                  a1286fc11cef        6 months ago        65.2MB
timonmat/xmr-stak-cpu   latest                  a1286fc11cef        6 months ago        65.2MB

ubuntu@ubuntu:~/Documents/docker/02_test$ docker rmi timonmat/xmr-stak-cpu:latest
Untagged: timonmat/xmr-stak-cpu:latest
Untagged: timonmat/xmr-stak-cpu@sha256:cd5357198ef52fbdb16a1db04f59661316bb6533782fda922a94f651bff92da1

ubuntu@ubuntu:~/Documents/docker/02_test$ docker images
REPOSITORY              TAG                     IMAGE ID            CREATED             SIZE
test/test               latest                  a1286fc11cef        6 months ago        65.2MB
```
