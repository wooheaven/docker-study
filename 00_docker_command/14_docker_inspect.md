# docker inspect
```{bash}
$ docker inspect --format "{{ json .Mounts }}" gitlab | python -m json.tool
[
    {
        "Destination": "/etc/gitlab",
        "Mode": "",
        "Propagation": "",
        "RW": true,
        "Source": "/home/rwoo/02_workspace/03_Git_Workspace/Local_GitLab_Workspace/srv/gitlab/config",
        "Type": "bind"
    },
    {
        "Destination": "/var/log/gitlab",
        "Mode": "",
        "Propagation": "",
        "RW": true,
        "Source": "/home/rwoo/02_workspace/03_Git_Workspace/Local_GitLab_Workspace/srv/gitlab/logs",
        "Type": "bind"
    },
    {
        "Destination": "/var/opt/gitlab",
        "Mode": "",
        "Propagation": "",
        "RW": true,
        "Source": "/home/rwoo/02_workspace/03_Git_Workspace/Local_GitLab_Workspace/srv/gitlab/data",
        "Type": "bind"
    }
]
```
