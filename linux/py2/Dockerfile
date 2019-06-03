FROM ubuntu:19.04

ENV DEBIAN_FRONTEND noninteractive

ARG PYINSTALLER_VERSION=3.4

# install python
RUN set -x \
    && apt-get update -qy \
    && apt-get install --no-install-recommends -qfy python python-dev python-pip python-setuptools build-essential libmysqlclient-dev git \
    && apt-get clean

# PYPI repository location
ENV PYPI_URL=https://pypi.python.org/
# PYPI index location
ENV PYPI_INDEX_URL=https://pypi.python.org/simple

# install pyinstaller
RUN if [ -z $PYINSTALLER_VERSION ];\
        then pip install pyinstaller;\
        else pip install pyinstaller==$PYINSTALLER_VERSION;\
    fi

RUN mkdir /src/
VOLUME /src/
WORKDIR /src/

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
