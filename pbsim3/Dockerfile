# Using Ubuntu's base image
FROM ubuntu:noble-20250127

# Adding labels for the GitHub Container Registry
LABEL org.opencontainers.image.title="PBSIM3"
LABEL org.opencontainers.image.description="Container image for the use of PBSIM3: a simulator for all types of PacBio and ONT long reads"
LABEL org.opencontainers.image.version="3.0.5"
LABEL org.opencontainers.image.authors="Sanaz01"
LABEL org.opencontainers.image.source=https://github.com/egenesis/docker-library/pbsim3


# Install dependencies
RUN apt-get update && \
    apt-get install -y \
    build-essential \
    wget \
    make \
    libncurses5-dev \
    libncursesw5-dev \
    libcurl4-openssl-dev \
    zlib1g-dev \
    liblzma-dev \
    libbz2-dev \
    vim \
    && rm -rf /var/lib/apt/lists/*

# Install samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.21/samtools-1.21.tar.bz2 && \
    tar -xvjf samtools-1.21.tar.bz2 && \
    rm samtools-1.21.tar.bz2

WORKDIR samtools-1.21
RUN make && \
    make install

WORKDIR /

# Install PBSIM3_v3.0.5, all models are stored in /pbsim3-3.0.5/data
RUN wget https://github.com/yukiteruono/pbsim3/archive/refs/tags/v3.0.5.tar.gz && \
    tar -xzf v3.0.5.tar.gz && \
    rm v3.0.5.tar.gz


# Set the working directory
WORKDIR /pbsim3-3.0.5

RUN ./configure && \
    make && \
    make install

WORKDIR /
