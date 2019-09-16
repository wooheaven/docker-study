# cpus 4 and cpus 3
```
$ docker run -itd --rm --cpus="4" \
--name spark ubuntu:16.04_4th_spark_yarn

$ docker inspect spark | grep Cpu
            "CpuShares": 0,
            "NanoCpus": 4000000000,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "CpuCount": 0,
            "CpuPercent": 0,

$ docker run -itd --rm --cpus="3" \
--name spark ubuntu:16.04_4th_spark_yarn

$ docker inspect spark | grep Cpu
            "CpuShares": 0,
            "NanoCpus": 3000000000,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "CpuCount": 0,
            "CpuPercent": 0,
```

# ref link
[moby source code link](https://github.com/moby/moby/blob/v1.12.0-rc4/daemon/cluster/executor/container/container.go#L328-L332)
