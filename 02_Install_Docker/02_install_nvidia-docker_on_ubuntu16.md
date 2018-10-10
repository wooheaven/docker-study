# ref 
```
https://github.com/NVIDIA/nvidia-docker
```

# If you have nvidia-docker 1.0 installed: we need to remove it and all existing GPU containers
```
docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
sudo apt-get purge -y nvidia-docker
```

# Add the package repositories
```
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update
```

# Install nvidia-docker2 and reload the Docker daemon configuration
```
sudo apt-get install -y nvidia-docker2
sudo pkill -SIGHUP dockerd
```

# Test nvidia-smi with the latest official CUDA image
```
docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi
```

# real log
```
ubuntu@ubuntu:~$ docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f

ubuntu@ubuntu:~$ sudo apt-get purge -y nvidia-docker
[sudo] password for ubuntu:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package nvidia-docker

ubuntu@ubuntu:~$ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
OK

ubuntu@ubuntu:~$ curl -s -L https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
deb https://nvidia.github.io/libnvidia-container/ubuntu16.04/amd64 /
deb https://nvidia.github.io/nvidia-container-runtime/ubuntu16.04/amd64 /
deb https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64 /

ubuntu@ubuntu:~$ sudo apt-get update
Get:1 https://nvidia.github.io/libnvidia-container/ubuntu16.04/amd64  InRelease [1,106 B]
Get:2 https://nvidia.github.io/nvidia-container-runtime/ubuntu16.04/amd64  InRelease [1,103 B]
Get:3 https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64  InRelease [1,096 B]
Get:4 https://nvidia.github.io/libnvidia-container/ubuntu16.04/amd64  Packages [2,784 B]
Get:5 https://nvidia.github.io/nvidia-container-runtime/ubuntu16.04/amd64  Packages [3,604 B]
Get:6 https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64  Packages [4,200 B]
Hit:7 https://download.docker.com/linux/ubuntu xenial InRelease
Hit:8 http://kr.archive.ubuntu.com/ubuntu xenial InRelease
Hit:9 http://kr.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:10 http://kr.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:11 http://security.ubuntu.com/ubuntu xenial-security InRelease
Fetched 13.9 kB in 13s (1,010 B/s)
Reading package lists... Done

ubuntu@ubuntu:~$ sudo apt-get install -y nvidia-docker2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  libnvidia-container-tools libnvidia-container1 nvidia-container-runtime
The following NEW packages will be installed:
  libnvidia-container-tools libnvidia-container1 nvidia-container-runtime nvidia-docker2
0 upgraded, 4 newly installed, 0 to remove and 98 not upgraded.
Need to get 2,044 kB of archives.
After this operation, 9,755 kB of additional disk space will be used.
Get:1 https://nvidia.github.io/libnvidia-container/ubuntu16.04/amd64  libnvidia-container1 1.0.0~alpha.3-1 [54.3 kB]
Get:2 https://nvidia.github.io/libnvidia-container/ubuntu16.04/amd64  libnvidia-container-tools 1.0.0~alpha.3-1 [14.5 kB]
Get:3 https://nvidia.github.io/nvidia-container-runtime/ubuntu16.04/amd64  nvidia-container-runtime 1.1.1+docker17.12.0-1 [1,972 kB]
Get:4 https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64  nvidia-docker2 2.0.2+docker17.12.0-1 [2,782 B]
Fetched 2,044 kB in 12s (165 kB/s)
Selecting previously unselected package libnvidia-container1:amd64.
(Reading database ... 59991 files and directories currently installed.)
Preparing to unpack .../libnvidia-container1_1.0.0~alpha.3-1_amd64.deb ...
Unpacking libnvidia-container1:amd64 (1.0.0~alpha.3-1) ...
Selecting previously unselected package libnvidia-container-tools.
Preparing to unpack .../libnvidia-container-tools_1.0.0~alpha.3-1_amd64.deb ...
Unpacking libnvidia-container-tools (1.0.0~alpha.3-1) ...
Selecting previously unselected package nvidia-container-runtime.
Preparing to unpack .../nvidia-container-runtime_1.1.1+docker17.12.0-1_amd64.deb ...
Unpacking nvidia-container-runtime (1.1.1+docker17.12.0-1) ...
Selecting previously unselected package nvidia-docker2.
Preparing to unpack .../nvidia-docker2_2.0.2+docker17.12.0-1_all.deb ...
Unpacking nvidia-docker2 (2.0.2+docker17.12.0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Setting up libnvidia-container1:amd64 (1.0.0~alpha.3-1) ...
Setting up libnvidia-container-tools (1.0.0~alpha.3-1) ...
Setting up nvidia-container-runtime (1.1.1+docker17.12.0-1) ...
Setting up nvidia-docker2 (2.0.2+docker17.12.0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...

ubuntu@ubuntu:~$ sudo pkill -SIGHUP dockerd

ubuntu@ubuntu:~$ docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi
Unable to find image 'nvidia/cuda:latest' locally
latest: Pulling from nvidia/cuda
1be7f2b886e8: Pull complete
6fbc4a21b806: Pull complete
c71a6f8e1378: Pull complete
4be3072e5a37: Pull complete
06c6d2f59700: Pull complete
80a2fed119d9: Pull complete
4de9f14ac216: Pull complete
2bac07ac0aba: Pull complete
d172150d9f12: Pull complete
534b97146672: Pull complete
Digest: sha256:8a6a860f5f3bd3aff8926c84a4b5695e60b580b66d14eef13a50b3cbf1813168
Status: Downloaded newer image for nvidia/cuda:latest
Mon Jan 29 11:05:04 2018
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 384.111                Driver Version: 384.111                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 950M    Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   39C    P0    N/A /  N/A |      0MiB /  2002MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```
