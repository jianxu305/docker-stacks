# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=jupyter/scipy-notebook
FROM $BASE_CONTAINER

LABEL maintainer="Jupyter Project <jupyter@googlegroups.com>"

USER root
RUN apt-get update -y && \
    apt-get install -y xvfb && \
    apt-get install -y python-opengl

USER ${NB_USER}
RUN echo ${NB_USER}

# Install Tensorflow
RUN pip install --quiet --no-cache-dir \
    'tensorflow==2.3.1' && \
    pip install \
        gym \
        pyvirtualdisplay && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"
