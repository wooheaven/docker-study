Reference 

[nvidia CUDA + cuDNN DockerHub images] : https://hub.docker.com/r/nvidia/cuda/

[nvidia CUDA + cuDNN DockerFile] : https://gitlab.com/nvidia/cuda


```{bash}
$ # docker version check
$ docker --version
Docker version 17.09.0-ce, build afdb6d4
```

```{bash}
$ # Ubuntu:14.04
$ docker pull ubuntu:14.04
$ docker images
```

```{bash}
$ # nvidia/cuda:8.0-runtime-ubuntu14.04
$ cat Dockerfile-NC8-R-U14.04.txt
FROM ubuntu:14.04
LABEL maintainer "NVIDIA CORPORATION <cudatools@nvidia.com>"

RUN NVIDIA_GPGKEY_SUM=d1be581509378368edeec8c1eb2958702feedf3bc3d17011adbf24efacce4ab5 && \
    NVIDIA_GPGKEY_FPR=ae09fe4bbd223a84b2ccfce3f60f4b3d7fa2af80 && \
    apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1404/x86_64/7fa2af80.pub && \
    apt-key adv --export --no-emit-version -a $NVIDIA_GPGKEY_FPR | tail -n +2 > cudasign.pub && \
    echo "$NVIDIA_GPGKEY_SUM  cudasign.pub" | sha256sum -c --strict - && rm cudasign.pub && \
    echo "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1404/x86_64 /" > /etc/apt/sources.list.d/cuda.list

ENV CUDA_VERSION 8.0.61

ENV CUDA_PKG_VERSION 8-0=$CUDA_VERSION-1

# error
# debconf: unable to initialize frontend: Dialog
# debconf: (TERM is not set, so the dialog frontend is not usable.)
# debconf: falling back to frontend: Readline
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
        cuda-nvrtc-$CUDA_PKG_VERSION \
        cuda-nvgraph-$CUDA_PKG_VERSION \
        cuda-cusolver-$CUDA_PKG_VERSION \
        cuda-cublas-8-0=8.0.61.2-1 \
        cuda-cufft-$CUDA_PKG_VERSION \
        cuda-curand-$CUDA_PKG_VERSION \
        cuda-cusparse-$CUDA_PKG_VERSION \
        cuda-npp-$CUDA_PKG_VERSION \
        cuda-cudart-$CUDA_PKG_VERSION && \
    ln -s cuda-8.0 /usr/local/cuda && \
    rm -rf /var/lib/apt/lists/*

# nvidia-docker 1.0
LABEL com.nvidia.volumes.needed="nvidia_driver"
LABEL com.nvidia.cuda.version="${CUDA_VERSION}"

RUN echo "/usr/local/nvidia/lib" >> /etc/ld.so.conf.d/nvidia.conf && \
    echo "/usr/local/nvidia/lib64" >> /etc/ld.so.conf.d/nvidia.conf

ENV PATH /usr/local/nvidia/bin:/usr/local/cuda/bin:${PATH}
ENV LD_LIBRARY_PATH /usr/local/nvidia/lib:/usr/local/nvidia/lib64

# nvidia-container-runtime
ENV NVIDIA_VISIBLE_DEVICES all
ENV NVIDIA_DRIVER_CAPABILITIES compute,utility
ENV NVIDIA_REQUIRE_CUDA "cuda>=8.0"

$ docker build -t nvidia/cuda:8.0-runtime-ubuntu14.04 -f Dockerfile-NC8-R-U14.04.txt .
$ docker images
```

```{bash}
$ # nvidia/cuda:8.0-runtime-cudnn6-ubuntu14.04
$ cat Dockerfile-NC8-R-cuDNN6-U14.04.txt
ARG repository
FROM ${repository}:8.0-runtime-ubuntu14.04
LABEL maintainer "NVIDIA CORPORATION <cudatools@nvidia.com>"

RUN echo "deb http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1404/x86_64 /" > /etc/apt/sources.list.d/nvidia-ml.list

ENV CUDNN_VERSION 6.0.21
LABEL com.nvidia.cudnn.version="${CUDNN_VERSION}"

# error
# debconf: unable to initialize frontend: Dialog
# debconf: (TERM is not set, so the dialog frontend is not usable.)
# debconf: falling back to frontend: Readline
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
            libcudnn6=$CUDNN_VERSION-1+cuda8.0 && \
    rm -rf /var/lib/apt/lists/*

$ docker build -t nvidia/cuda:8.0-runtime-cudnn6-ubuntu14.04 --build-arg repository=nvidia/cuda -f Dockerfile-NC8-R-cuDNN6-U14.04.txt .
$ docker images
```

```{bash}
$ # nvidia/cuda:test
$ cat Dockerfile-test.txt
ARG repository
ARG JPASSWD
FROM ${repository}:8.0-runtime-cudnn6-ubuntu14.04

# bash shell
SHELL ["/bin/bash", "-c"]

# install anaconda3
RUN apt-get update && apt-get install -y wget vim && rm -rf /var/lib/apt/lists/*
RUN wget -q https://repo.continuum.io/archive/Anaconda3-5.0.1-Linux-x86_64.sh
RUN chmod +x Anaconda3-5.0.1-Linux-x86_64.sh
RUN /bin/bash Anaconda3-5.0.1-Linux-x86_64.sh -b -p /root/anaconda3
RUN echo 'export PATH="$PATH:/root/anaconda3/bin"' >> /root/.bashrc
ENV PATH $PATH:/root/anaconda3/bin
RUN echo $PATH

# conda create env
RUN conda create --name python354 python=3.5.4 -y

# conda install package
RUN source activate python354 && conda install -y pandas numpy ipython jupyter matplotlib scipy scikit-learn pillow h5py pydot graphviz && conda info --envs
RUN source activate python354 && conda list

# conda install tensorflow_gpu
RUN source activate python354 && pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.4.0-cp35-cp35m-linux_x86_64.whl
RUN source activate python354 && conda list

# conda install package
RUN source activate python354 && conda install -y keras && python -c 'import keras; print(keras.__version__)'
RUN cat /root/.keras/keras.json
RUN source activate python354 && conda list

# conda install protobuf
RUN source activate python354 && pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/protobuf-3.1.0-cp35-none-linux_x86_64.whl
RUN source activate python354 && conda list

# jupyter notebook config
RUN source activate python354 && jupyter notebook --generate-config --allow-root
RUN cp /root/.jupyter/jupyter_notebook_config.py /root/.jupyter/jupyter_notebook_config.bak

# jupyter notebook passwd
RUN echo ${JPASSWD} > /root/.jupyter/tmp1.txt
RUN source activate python354 && ipython -c "from IPython.lib import passwd; f = open('/root/.jupyter/tmp1.txt'); line = f.readline(); print(passwd(line))" > /root/.jupyter/tmp2.txt
RUN echo "c.NotebookApp.password = ""'"`cat /root/.jupyter/tmp2.txt`"'" > /root/.jupyter/jupyter_notebook_config.py
RUN cat /root/.jupyter/jupyter_notebook_config.py
RUN rm /root/.jupyter/tmp[1-2].txt

$ docker build -t nvidia/cuda:test --build-arg repository=nvidia/cuda --build-arg JPASSWD=test -f Dockerfile-test .
$ docker images
```

```{bash}
nvidia-docker run -it -p 8888:8888 -v /home/ubuntu/Downloads/workspace/:/root/workspace/ --name="test" nvidia/cuda:test /bin/bash
```

```{bash}
$ docker start test
$ docker attache test
$ docker exec -it test /bin/bash

$ jupyter notebook --notebook-dir=/root/workspace/ --no-browser --ip=0.0.0.0 --allow-root
```
