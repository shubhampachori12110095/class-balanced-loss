# Docker image for running TPU tensorflow examples.
FROM ubuntu:bionic

RUN apt-get update && apt-get install -y --no-install-recommends \
        curl \
        wget \
        sudo \
        gnupg \
        lsb-release \
        ca-certificates \
        build-essential \
        git \
        python \
        python-pip \
        python-setuptools && \
    export CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)" && \
    echo "deb https://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" > /etc/apt/sources.list.d/google-cloud-sdk.list && \
    curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - && \
    apt-get update && \
    apt-get install -y google-cloud-sdk && \
    pip install tensorflow==1.11 && \
    pip install google-cloud-storage

# Checkout tensorflow/models at the appropriate branch
RUN git clone -b r1.11 --depth 1 https://github.com/tensorflow/models.git /tensorflow_models

# Checkout tensorflow/tpu at the appropriate branch
RUN git clone -b r1.11 --depth 1 https://github.com/tensorflow/tpu.git /tensorflow_tpu_models
