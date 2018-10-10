# Document of Docker CLI(docker)
[Docker](https://www.docker.com)  
╠═1. [html document in korean](http://www.pyrasis.com/docker.html)  
╠═2. install  
║&ensp; ╠═2.1 [on Ubuntu14](02_Install_Docker/00_on_ubuntu14.md)  
║&ensp; ╠═2.2 [on Ubuntu16](02_Install_Docker/01_on_ubuntu16.md)  
║&ensp; ╚═2.3 [nvidia-docker on Ubuntu16](02_Install_Docker/02_install_nvidia-docker_on_ubuntu16.md)  
╚═3. [Command Line Interface](https://docs.docker.com/engine/reference/commandline/docker/)  
&ensp; &ensp; ╚═3.1. [exec](https://docs.docker.com/engine/reference/commandline/exec/)  
&ensp; &ensp; &ensp; &ensp; ╚═3.1.1. [ps -aef](03_Docker_CLI/01_docker_exec.md)  
( ║ ╠ ═ ╚ ) 

# tmp Contents Table
| Head            | Contents                                                                                                         |
|-----------------|------------------------------------------------------------------------------------------------------------------|
| Docker Command  | [docker images](00_docker_command/01_docker_images.md)                                                           |
|                 | [docker search](00_docker_command/02_docker_search.md)                                                           |
|                 | [docker pull](00_docker_command/03_docker_pull.md)                                                               |
|                 | [docker run](00_docker_command/04_docker_run.md)                                                                 |
|                 | [docker ps](00_docker_command/05_docker_ps.md)                                                                   |
|                 | [docker port](00_docker_command/06_docker_port.md)                                                               |
|                 | [docker attach](00_docker_command/07_docker_attach.md)                                                           |
|                 | [docker start](00_docker_command/08_docker_start.md)                                                             |
|                 | [docker exit](00_docker_command/09_docker_exit.md)                                                               |
|                 | [docker commit](00_docker_command/10_docker_commit.md)                                                           |
|                 | [docker pull BusyBox in order to mount on postgres-Container](00_docker_command/11_BusyBox_on_docker.md)         |
|                 | [docker create volumn](00_docker_command/12_docker_volumn.md)                                                    |
|                 | [install gitlab on docker](00_docker_command/13_gitlab_ce_on_docker.md)                                          |
|                 | [docker inspect](00_docker_command/14_docker_inspect.md)                                                         |
|                 | [docker copy](00_docker_command/15_docker_cp.md)                                                                 |

# [docker build](00_docker_command/16_docker_build.md)
```{bash}
$ docker build -t image:tag -f Dockerfile .
$ docker images
```

# [docker save](00_docker_command/17_docker_save.md)
# [docker load](00_docker_command/18_docker_load.md)
# [docker tag](00_docker_command/19_docker_tag.md)
