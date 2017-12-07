FROM lightwalking/alpine-mpich:onbuild

# # ------------------------------------------------------------
# # Build MPI project
# # ------------------------------------------------------------

# Put all build steps and additional package installation here

# Note: the current directory is ${WORKDIR:=/project}, which is
# also the default directory where ${USER:=mpi} will SSH login to
USER ${USER}

# Copy the content of `project` directory in the host machine to 
# the current working directory in this Docker image
COPY project/ .

RUN sudo apk add python \
	&& sudo chown -R ${USER}:${USER} ./ \
	&& chmod +x run.py \
	&& cd mpi-hello-world && make \
	&& cd ../mpi-send-and-receive && make \
	&& cd ../dynamic-receiving-with-mpi-probe-and-mpi-status && make \
	&& cd ../point-to-point-communication-application-random-walk && make \
	&& cd ../mpi-broadcast-and-collective-communication && make \
	&& cd ../mpi-scatter-gather-and-allgather && make \
	&& cd ../performing-parallel-rank-with-mpi && make \
	&& cd ../mpi-reduce-and-allreduce && make \
	&& cd ../introduction-to-groups-and-communicators && make

# Normal build command
RUN mpicc -o mpi_hello_world mpi_hello_world.c

# ####################
# For Docker beginner:

# After Docker syntax `RUN`, you can execute any command available in 
# the current shell of the image.

# To switch to root:    USER root
# To switch back to default user: USER ${USER}
