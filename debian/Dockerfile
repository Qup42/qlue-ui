# Note: identical to the qlever-ui build container
ARG BASE_IMAGE=debian:13-slim

FROM ${BASE_IMAGE}
LABEL org.opencontainers.image.authors="Julian Mundhahs <mundhahj@tf.uni-freiburg.de>"

RUN apt update && apt upgrade -y
# general packages for building python packages
RUN apt install -y python3 dpkg git debhelper-compat dh-python python3-all python3-build python3-setuptools python3-dev
# debug tools and helpers
RUN apt install -y vim devscripts
# qlue-ui
RUN apt install -y dh-virtualenv python3-venv curl
# Install the latest nodejs/npm LTS via a custom repo because qlue-ui (for whatever reason) requires a very current version.
RUN curl -fsSL https://deb.nodesource.com/setup_24.x | bash -
# This custom nodejs also provides npm.
RUN apt update && apt install -y nodejs
RUN git config --global user.email "mundhahj@tf.uni-freiburg.de" && git config --global user.name "Julian Mundhahs"
# aliases for the actions that do the building
COPY tools_build.sh /root/tools_build.sh

WORKDIR /app
