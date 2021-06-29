# syntax=docker/dockerfile:1
FROM ubuntu:20.04
RUN apt-get update && \
    apt-get install -y wget && \
    rm -rf /var/lib/apt/lists/*
WORKDIR /tmp
RUN wget -O- https://sourceforge.net/projects/bio-bwa/files/bwakit/bwakit-0.7.15_x64-linux.tar.bz2/download \
        | bzip2 -dc | tar xf -
RUN wget -O- https://github.com/lh3/bwa/archive/refs/tags/v0.7.17.tar.gz \
        | gzip -dc  | tar xf - && \
    cp bwa-0.7.17/bwakit/* bwa.kit/ && \
    rm -rf bwa-0.7.17

FROM ubuntu:20.04
LABEL org.opencontainers.image.source=https://github.com/gandallab/containers
RUN apt-get update && \
    apt-get install -y perl && \
    rm -rf /var/lib/apt/lists/*
COPY --from=0 /tmp/bwa.kit /opt/bwa.kit/