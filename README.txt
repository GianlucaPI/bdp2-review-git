This repository includes the Dockerfile to build an image that uses Redis without installation (pip install redi).

FROM jupyter/minimal-notebook #this command says that we want to start from the already existing image (jupyter/minimal-notebook)
RUN pip install redis #this command says that we execute the specified shell command (pip install redis). Redis will be installed on the image we created, so that we can start a new python project without installing it manually.

