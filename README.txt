Thanks to this project, it is possible to run a complete environment for development. This environment will used jupyter notebook and redis. 

This repository includes:
 - the Dockerfile to build an image that uses Redis without installation (pip install redis).

 	-FROM jupyter/minimal-notebook ##this command says that we want to start from the already existing image (jupyter/minimal-notebook)

	-RUN pip install redis ##this command says that we execute the specified shell command (pip install redis). Redis will be installed on the image we created, so that we can start a new python project without installing it manually.

 - the docker-compose.yml file:

	-networks: bdp2-net ## this is the custom bridge used to connect all the containers. In case the bdp2-net is removed ( docker network remove bdp-net ), the docker-compose will automatically create a new bridge.

        -jupyter image ## taken from the image extendend starting from minimal-notebook. This will be pulled from my own repository on DockerHub
	redis service

 	-ports: 8888 of the virtual machine hosting the service is mapped to 8888 port of the container. In order to use the jupyter service we should specify this port.
		9000 of the virtual machine hosting the service is mapped to 9000 port of the container. In order to use the portainer service we should specify this port. 

	In order to use the https protocol (instead of http), the flag GEN_CERT=yes in the "environment" section of the jupyter service has been added. Otherwise, the http will be used instead.
	No certificate is installed at the moment, so it will be shown as "not secure" even if we use that flag.
