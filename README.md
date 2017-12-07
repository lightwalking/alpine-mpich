# Alpine MPICH

[Raspberry Pi](https://www.raspberrypi.org/) armhf compatible Docker image of Alpine Linux with [MPICH](http://www.mpich.org/) -- portable implementation of Message Passing Interface (MPI) standard. Designed for MPI program development and deployment.

Push to Docker Hub [https://hub.docker.com/r/lightwalking/alpine-mpich](https://hub.docker.com/r/lightwalking/alpine-mpich/)

[![Docker Hub](http://dockeri.co/image/lightwalking/alpine-mpich)](https://hub.docker.com/r/lightwalking/alpine-mpich)


`base image` ([Dockerfile](https://github.com/lightwalking/alpine-mpich/blob/master/Dockerfile)) : contains MPICH and essential build tools. Intended to be used as development environment for developing MPI programs.

`onbuild image` ([Dockerfile](https://github.com/lightwalking/alpine-mpich/blob/onbuild/Dockerfile)) : inherits base image with network setup for cluster. Can be used like base image but intended to be used to build image that contains compiled MPI program in order to deploy to a cluster.

`cluster` ([project scaffolder](https://github.com/lightwalking/alpine-mpich/tree/master/cluster)) : is a directory containing a setup for deploying MPI programs to a cluster of containers. Include a runner script to automate Docker commands.


*Below is instruction for building the Docker image yourself if you don't want to use the pre-built base or onbuild image.*

----

## Build Instruction

The armhf images are prebuilt and hosted at Docker Hub, but in case you want to build them yourself:

```sh
$ git clone https://github.com/lightwalking/alpine-mpich

$ cd alpine-mpich

$ docker build -t lightwalking/alpine-mpich base/

$ docker build -t lightwalking/alpine-mpich:onbuild onbuild/
```
