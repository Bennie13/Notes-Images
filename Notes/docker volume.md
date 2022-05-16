# **docker volume**
- Loading data from containers to local and local to containers

## using cmd
- `docker run -it -v` Auto sync file in two paths, only need to change locally
	- `-v` volumes
		- ``"/host path:container path"` 
		- `volume name:container path`
		-  `container path`
- `docker volume ls`
- `docker volume inspect "volume name"`

## Dockerfile
Using dockerfile to create an image.
```shell
FROM          # indicating basic image
MAINTAINER    
RUN    
ADD
WORKDIR
VOLUME
EXPOSE        # port config
RUN
CMD           # replace
ENTRYPOINT    # append
ONBUILD       # inherit
COPY
ENV
```

```shell
FROM centos
VOLUME ["volume01", "volume02"]
CMD echo "---------end-----------"
CMD bin/bash
```
- `docker build -f "path of dockerfile" -t "image name:[TAG] ."`
>`docker run -it --privileged --pid=host debian nsenter -t 1 -m -u -n -i sh` check if it sync or not in MacOS if not specific host path



## volume container
sync bwtween two containers.
- `docker run --volumes-from "container name" "image name"` 