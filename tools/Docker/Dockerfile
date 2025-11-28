FROM ubuntu:20.04

# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Update and install dependencies
RUN apt-get update && \
    apt-get install -y \
    python3-pip \
    python3-can \
    python3-serial \
    python3-setuptools \
    python3-pyelftools \
    python3-qtpy \
    python3-wheel \
    libtinfo5 \
    curl \
    patch \
    git && \
    pip3 install pep517

# Set up user
ARG USER_ID
ARG GROUP_ID
RUN if ! getent group $GROUP_ID; then groupadd -g $GROUP_ID usergroup; fi && \
    if ! id -u $USER_ID > /dev/null 2>&1; then useradd -m -u $USER_ID -g $GROUP_ID -s /bin/bash user; fi && \
    chown -R $USER_ID:$GROUP_ID /home/user

# Switch to non-root user
USER user

# Set working directory
WORKDIR /src