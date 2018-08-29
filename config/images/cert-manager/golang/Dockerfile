# Includes golang and some extra tools
FROM golang:1.9.3
LABEL maintainer="james@jetstack.io"

# add env we can debug with the image name:tag
ARG IMAGE_ARG
ENV IMAGE=${IMAGE_ARG}

RUN apt-get update && apt-get install -y \
    python \
    rsync \
    wget && \
    apt-get clean

RUN curl -Lo helm.tar.gz https://storage.googleapis.com/kubernetes-helm/helm-v2.10.0-linux-amd64.tar.gz && \
    tar xvf helm.tar.gz && \
    mv linux-amd64/helm /usr/local/bin && \
    curl -Lo /usr/local/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/v1.9.10/bin/linux/amd64/kubectl && \
    chmod +x /usr/local/bin/kubectl

RUN curl -L https://github.com/golang/dep/releases/download/v0.4.1/dep-linux-amd64 >/tmp/dep \
    && curl -L https://github.com/mikefarah/yaml/releases/download/1.13.1/yaml_linux_amd64 >/tmp/yaml \
    && curl -L vert https://github.com/Masterminds/vert/releases/download/v0.1.0/vert-v0.1.0-linux-amd64 >/tmp/vert \
    && chmod +x /tmp/dep \
    && chmod +x /tmp/yaml \
    && chmod +x /tmp/vert \
    && mv /tmp/dep /tmp/yaml /tmp/vert /usr/local/bin/
RUN go get -v golang.org/x/tools/cmd/goimports

WORKDIR /workspace
