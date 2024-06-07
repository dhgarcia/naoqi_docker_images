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

## loading the naoqi docker image from the tar file

Download the docker image tar file from the images/ folder and run:

```shell
# naoqi 2.5.5
docker load -i naoqi-2-5-5.tar.gz

# naoqi 2.8.6
docker load -i naoqi-2-8-6.tar.gz

```

## running choregraphe in the docker container

```shell
# naoqi 2.5.5
docker run -it --rm --net=host --env=DISPLAY=$DISPLAY --volume='/tmp/.X11-unix:/tmp/.X11-unix:rw' --device=/dev/dri:/dev/dri naoqi:2.5.5 choregraphe

# naoqi 2.8.6
docker run -it --rm --net=host --env=DISPLAY=$DISPLAY --volume='/tmp/.X11-unix:/tmp/.X11-unix:rw' --device=/dev/dri:/dev/dri naoqi:2.8.6 choregraphe

```