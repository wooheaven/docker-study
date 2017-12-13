Reference 

[nvidia CUDA + cuDNN DockerHub images] : https://hub.docker.com/r/nvidia/cuda/

[nvidia CUDA + cuDNN DockerFile] : https://gitlab.com/nvidia/cuda

[Installing TensorFlow on Ubuntu] : https://www.tensorflow.org/install/install_linux

[TensorFlow binary Images] : https://hub.docker.com/r/tensorflow/tensorflow/tags/

# docker version check
```{bash}
docker --version
Docker version 17.09.0-ce, build afdb6d4
```

# Ubuntu:16.04
```{bash}
docker pull ubuntu:16.04
docker images
```

# build tensorflow/tensorflow:latest
```{bash}
cat Dockerfile # ref : https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/docker/Dockerfile
docker build -t tensorflow/tensorflow:latest -f Dockerfile .
docker images
```

# pull tensorflow/tensorflow:latest
```{bash}
$ docker pull tensorflow/tensorflow:latest
$ docker images
```

# docker run
```{bash}
docker run -it -p 8888:8888 -p 6006:6006 -e PASSWORD=passwd -v /home/ubuntu/Downloads/workspace/:/notebooks/ --name="test" tensorflow/tensorflow:latest /bin/bash
```

# nvidia-docker run
```{bash}
nvidia-docker run -it -p 8888:8888 -p 6006:6006 -e PASSWORD=passwd -v /home/ubuntu/Downloads/workspace/:/notebooks/ --name="test" nvidia/cuda:test /bin/bash
```

```{bash}
$ docker start test
$ docker attache test
$ docker exec -it test /bin/bash
```
