# docker
- 环境配置打包
- 跨平台
## History
1. 2010， `dotcloud`Corp offers`Pass`--Container tech
2. 2013，Open Source Code
3. 2014.9， Docker1.0
>What is LXC?

## Advantages
- DevOps
- Resource Scaling

## Structure
- image: information about how to build a container
- container: where apps run
- repository: Store images
- Client-Server structure, Using socket to connect
## cli
- `docker run hello-world`
- `docker version`
- `docker info`
- `docker stats` info about cpu

### images
-  `docker images`
- `docker search mysql`
- `docker pull mysql:tag` 分层下载，联合文件系统
- `docker rmi -f ` rm images ID or NAME
	- `docker rmi -f $(docker images -aq)` 

### container 
- `docker pull centos`
- `docker run [args] image`
	- ``--name="Name"
	- `-d` running in background
	- `-it` intereacting with container, further look some files in the container
	- `-p` indicating `container port
- `docker exec -it "container ID" "bin/bash"` Entering a runing container( intereactive terminal tab)
- `docker attach "container ID"`  Entering a runing container(seeing the output)
- `docker ps `
	- `-a` ALL containers running and ran
	- `-n=?` number of containers to be showed

- `exit` Terminatng
- `ctrl + p + q` exit without terminating

- `docker rm -f $(docker ps -aq)`
- `docker start "container ID"`
- `docker stop "container ID"`
- `docker kill "container ID"`
- `docker logs -tf --tail "number" "container ID"`
	>docker run -d centos -c "While true;do echo bowen;sleep 2;done"


| 命令 | 作用|
| :-- | :--|
| `docker cp "container ID:container path" "host path"`|copy files|
|`docker inspect "container ID"`|meta data of a container|
|`docker top "container ID"`|process in a container|

## Docker Image
- **UnionFS**: Treat files as multipel layers structure
![|400](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@master/Images/202205101826396.png)
>Your own image = what you do in container level + original image
-  `docker commit -m="" -a="Author" "container ID" "container name:[TAG]"`