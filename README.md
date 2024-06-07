# naoqi_docker_images
Docker images for naoqi 2.5 and 2.8 to work with NAO and PEPPER robots



## build the naoqi image with the dockerfile

Download the dockerfile from the dockerfiles/ folder and run:

```shell
# naoqi 2.5.5
DOCKER_BUILDKIT=1 docker build -t naoqi:2.5.5 -f Dockerfile.naoqi-2.5 .


# naoqi 2.8.6
DOCKER_BUILDKIT=1 docker build -t naoqi:2.8.6 -f Dockerfile.naoqi-2.8 .

```

The dockerfiles has been tested for naoqi versions 2.5.5 and 2.8.6.
It could be possible to build images for other versions (but not tested) by changing some of the ARG in the dockerfile.


```Markdown
# In dockerfile.naoqi-2.5 you can try chaning VERSION, SDK_VERSION, CHOREGRAPHE_VERSION

# 2.5.5
ARG VERSION="2.5.5.5-linux64"
ARG SDK_VERSION="2.5.5/sdk-python"
ARG CHOREGRAPHE_VERSION="2.5.5/Choregraphe"

# 2.5.10
ARG VERSION="2.5.10.7-linux64"
ARG SDK_VERSION="2.5.10/Python%20SDK"
ARG CHOREGRAPHE_VERSION="2.5.10/Choregraphe"

# 2.1.4
ARG VERSION="2.1.4.13-linux64"
ARG SDK_VERSION="2.1.4.13/sdk-python"
ARG CHOREGRAPHE_VERSION="2.1.4.13/choregraphe"

# In dockerfile.naoqi-2.8 you can try chaning VERSION, VERSION_FULL, SDK_BUILD

# 2.8.6
ARG VERSION="2.8.6"
ARG VERSION_FULL="2.8.6.23-linux64"
ARG SDK_BUILD="20191127_152327"

# 2.8.7
ARG VERSION="2.8.7/Python+SDK"
ARG VERSION_FULL="2.8.7.4-linux64"
ARG SDK_BUILD="20210819_141148"

# 2.8.5
ARG VERSION="2.8.5"
ARG VERSION_FULL="2.8.5.10-linux64"
ARG SDK_BUILD="20181203_200915"
```



## loading the naoqi docker image from the tar file

As an alternative to building the docker image you can download the pre-built images and load them.

Download the docker image tar file from the images/ folder and run:

```shell
# naoqi 2.5.5
docker load -i naoqi-2-5-5.tar.gz

# naoqi 2.8.6
docker load -i naoqi-2-8-6.tar.gz

```

## running choregraphe in the docker container

```shell
xhost + local:docker  #to allow docker to run GUI applications

# naoqi 2.5.5
docker run -it --rm --net=host --env=DISPLAY=$DISPLAY --volume='/tmp/.X11-unix:/tmp/.X11-unix:rw' --device=/dev/dri:/dev/dri naoqi:2.5.5 choregraphe

# naoqi 2.8.6
docker run -it --rm --net=host --env=DISPLAY=$DISPLAY --volume='/tmp/.X11-unix:/tmp/.X11-unix:rw' --device=/dev/dri:/dev/dri naoqi:2.8.6 choregraphe

```

