# syntax=docker/dockerfile:1

ARG SMRT_VER=smrtlink_8.0.0.80529

FROM ubuntu:20.04
ARG SMRT_VER
RUN apt-get update && apt-get install -y \
    wget \
    unzip \
    && rm -rf /var/lib/apt/lists/*
WORKDIR /tmp
RUN wget https://downloads.pacbcloud.com/public/software/installers/${SMRT_VER}.zip && \
    unzip ${SMRT_VER}.zip

FROM ubuntu:20.04
ARG SMRT_VER
LABEL org.opencontainers.image.source=https://github.com/gandallab/containers
RUN apt-get update && apt-get install -y \
    rsync \
    locales \
    && rm -rf /var/lib/apt/lists/*
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && locale-gen
ENV SMRT_ROOT=/opt/pacbio/smrtlink
COPY --from=0 /tmp/${SMRT_VER}.run /tmp/
RUN /tmp/${SMRT_VER}.run --rootdir $SMRT_ROOT --smrttools-only && \
    rm /tmp/${SMRT_VER}.run
ENV PATH="${SMRT_ROOT}/smrtcmds/bin:${PATH}"
