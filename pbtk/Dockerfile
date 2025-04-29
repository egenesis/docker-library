# Using miniconda base image
FROM continuumio/miniconda3:25.1.1-2

# Adding labels for the GitHub Container Registry
LABEL org.opencontainers.image.title="pbtk"
LABEL org.opencontainers.image.description="Container image for the use of PacBio BAM toolkit"
LABEL org.opencontainers.image.version="3.5.0"
LABEL org.opencontainers.image.authors="Sanaz01"
LABEL org.opencontainers.image.source=https://github.com/egenesis/docker-library

# Set the shell option to fail if any command in a pipe fails
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install prerequisites
RUN apt-get update \
    && rm -rf /var/lib/apt/lists/*

# Install only essential dependencies, avoid installing unnecessary packages globally
RUN conda update -n base -c defaults conda && \
    conda clean --all --yes && \
    rm -rf /opt/conda/pkgs/* /root/.conda /root/.cache

# Installing pbtk (https://github.com/PacificBiosciences/pbtk)
RUN conda install -y -c bioconda pbtk=3.5.0

WORKDIR /app
