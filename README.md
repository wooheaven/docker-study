╠═1 install  
║░╠═1 [on Ubuntu14](01_Install_Docker/01_install_docker_on_ubuntu14.md)  
║░╠═2 [on Ubuntu16](01_Install_Docker/02_install_docker_on_ubuntu16.md)  
║░╠═3 [on Ubuntu18](01_Install_Docker/03_install_docker_on_ubuntu18.md)  
║░╚═4 [nvidia-docker on Ubuntu16](01_Install_Docker/04_install_nvidia-docker_on_ubuntu16.md)  
╠═2 [docker : Command Line Interface](https://docs.docker.com/engine/reference/commandline/docker/)  
║░╠═1 [attach](https://docs.docker.com/engine/reference/commandline/attach/)  
║░║░╚═1 [docker attach](02_Docker_CLI/01_attach/01_docker_attach.md)  
║░╠═2 [build](https://docs.docker.com/engine/reference/commandline/build/)  
║░║░╚═1 [Dockerfile](https://docs.docker.com/engine/reference/builder/#usage)  
║░║░░░╚═1 [ENV](https://docs.docker.com/engine/reference/builder/#env)  
║░║░░░░░╚═1 [docker build Dockerfile ENV](02_Docker_CLI/02_build/01_Dockerfile/01_ENV.md)  
║░╠═3 [commit](https://docs.docker.com/engine/reference/commandline/commit/)  
║░║░╚═1 [docker commit](02_Docker_CLI/03_commit/01_docker_commit.md)  
║░╠═4 [cp](https://docs.docker.com/engine/reference/commandline/cp/)  
║░║░╚═1 [docker copy](02_Docker_CLI/04_cp/01_docker_cp.md)  
║░╠═5 etc  
║░║░╚═1 [docker exit](02_Docker_CLI/05_etc/01_exit/01_docker_exit.md)  
║░╠═6 [exec](https://docs.docker.com/engine/reference/commandline/exec/)  
║░║░╚═1 [docker exec CONTAINER ps -aef](02_Docker_CLI/06_exec/01_docker_exec_CONTAINER_ps-aef.md)  
║░╠═7 [export](https://docs.docker.com/engine/reference/commandline/export/)  
║░║░╚═1 [docker export](02_Docker_CLI/07_export/01_docker_export.md)  
║░╠═8 [images](https://docs.docker.com/engine/reference/commandline/images/)  
║░║░╚═1 [docker images](02_Docker_CLI/08_images/01_docker_images.md)  
║░╠═9 [import](https://docs.docker.com/engine/reference/commandline/import/)  
║░║░╚═1 [docker import](02_Docker_CLI/09_import/01_docker_import.md)  
║░╠═10 [inspect](https://docs.docker.com/engine/reference/commandline/inspect/)  
║░║░╚═1 [docker inspect](02_Docker_CLI/10_inspect/01_docker_inspect.md)  
║░╠═11 [load](https://docs.docker.com/engine/reference/commandline/load/)  
║░║░╚═1 [docker load](02_Docker_CLI/11_load/01_docker_load.md)  
║░╠═12 [network](https://docs.docker.com/engine/reference/commandline/network/)  
║░║░╠═1 [create](https://docs.docker.com/engine/reference/commandline/network_create/)  
║░║░║░╠═1 docker network create [mynet --driver bridge --subnet 172.20.0.0/16 --ip-range 172.20.0.0/24 --gateway 172.20.0.1](02_Docker_CLI/12_network/01_create/01_docker_network_create_bridge.md) : manually defined network  
║░║░║░╚═2 docker network create [postgres-network](02_Docker_CLI/12_network/01_create/02_docker_network_create_pg-network.md) : default defined network  
║░║░╠═2 driver  
║░║░║░╠═1 docker network create mynet [--driver bridge](02_Docker_CLI/12_network/02_driver/01_bridge/01_docker_network_bridge.md) : a default driver of docker network  
║░║░║░╠═2 docker network create mynet [--driver container](02_Docker_CLI/12_network/02_driver/02_container/01_docker_network_container.md) : a driver of docker network  
║░║░║░╚═3 docker network create mynet [--driver host](02_Docker_CLI/12_network/02_driver/03_host/01_docker_network_host.md) : a driver of docker network  
║░║░╠═3 [inspect](https://docs.docker.com/engine/reference/commandline/network_inspect/)  
║░║░║░╚═1 docker network inspect [bridge](02_Docker_CLI/12_network/03_inspect/01_docker_network_inspect_bridge.md)  
║░║░╚═4 [ls](https://docs.docker.com/engine/reference/commandline/network_ls/)  
║░║░░░╚═1 docker network [ls](02_Docker_CLI/12_network/04_ls/02_docker_network_ls.md)  
║░╠═13 [port](https://docs.docker.com/engine/reference/commandline/port/)  
║░║░╚═1 docker [port](02_Docker_CLI/13_port/01_docker_port.md)  
║░╠═14 [ps](https://docs.docker.com/engine/reference/commandline/ps/)  
║░║░╚═1 docker [ps](02_Docker_CLI/14_ps/01_docker_ps.md)  
║░╠═15 [pull](https://docs.docker.com/engine/reference/commandline/pull/)  
║░║░╚═1 docker [pull](02_Docker_CLI/15_pull/01_docker_pull.md)  
║░╠═16 run [document](https://docs.docker.com/engine/reference/commandline/run/)  
║░║░╠═1 docker run [--cpus](02_Docker_CLI/16_run/01_docker_run_--cpus.md) : Number of CPUs  
║░║░╠═2 docker run [-it](02_Docker_CLI/16_run/02_docker_run_-it.md) : -i --interactive Keep STDIN open even if not attached, -t -tty Allocate a pseudo-TTY  
║░║░╠═3 docker run [--network](02_Docker_CLI/16_run/03_docker_run_-itd_--rm_--network_--ip_--add-host.md) : --network Connect a container to a network  
║░║░╠═4 docker run [--ip --add-host](02_Docker_CLI/16_run/03_docker_run_-itd_--rm_--network_--ip_--add-host.md) : -ip IPv4 address, --add-host Add a custom host-to-IP mapping (host:ip)  
║░║░╠═5 docker run [-p 127.0.0.1:9999:9999](02_Docker_CLI/16_run/04_docker_run_-p_-v.md) : -p --publish Publish a container's port(s) to the host  
║░║░╠═6 docker run [-v ./python_workspace:/home/python_workspace](02_Docker_CLI/16_run/04_docker_run_-p_-v.md) : -v --volume Bind mount a volume  
║░║░╠═7 docker run [--restart always](02_Docker_CLI/16_run/05_docker_run_--restart_always.md) : Always restart the container regardless of the exit status.  
║░║░╚═8 docker run [--volumes-from](02_Docker_CLI/16_run/06_docker_run_--volumes-from.md) : Mount volumes from the specified container(s)  
║░╠═17 [save](https://docs.docker.com/engine/reference/commandline/save/)  
║░║░╚═1 docker [save](02_Docker_CLI/17_save/01_docker_save.md)  
║░╠═18 [search](https://docs.docker.com/engine/reference/commandline/search/)  
║░║░╚═1 docker [search](02_Docker_CLI/18_search/01_docker_search.md)  
║░╚═19 [start](https://docs.docker.com/engine/reference/commandline/start/)  
║░║░╚═1 docker [start](02_Docker_CLI/19_start/01_docker_start.md)  
║░╚═20 [tag](https://docs.docker.com/engine/reference/commandline/tag/)  
║░░░╚═1 docker [tag](02_Docker_CLI/20_tag/01_docker_tag.md)  
╚═3 ETC  
░░╠═1 [docker pull busybox](03_ETC/01_docker_pull_busybox.md)  
░░║░╚═1 [docker data container image](https://hub.docker.com/_/busybox)  
░░╠═2 [dockerize mysql](03_ETC/02_dockerize_mysql.md)  
░░╠═3 [on docker container : install python3 and it's system package](03_ETC/03_install_python352_and_package_as_system_package_on_docker_container_ubuntu16.md)  
░░╠═4 [install gitlab on docker](03_ETC/04_gitlab_ce_on_docker.md)  
░░╚═5 [docker korean document](http://www.pyrasis.com/docker.html)  


# [docker build](00_docker_command/16_docker_build.md)
```{bash}
$ docker build -t image:tag -f Dockerfile .
$ docker images
```
