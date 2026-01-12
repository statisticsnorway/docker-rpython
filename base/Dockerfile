#syntax=docker/dockerfile:1

FROM docker.io/rocker/r2u:24.04

LABEL org.opencontainers.image.source=https://github.com/statisticsnorway/docker-rpython
LABEL org.opencontainers.image.description="Container for running both python and R, based on r2u."
LABEL org.opencontainers.image.licenses=MIT

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        micro \
        nano \
        pipx \
        python3-dev \
        python3-pip \
        python3-venv \
        r-cran-dplyr \
        r-cran-gausssuppression \
        r-cran-httpgd \
        r-cran-languageserver \
        r-cran-modsem \
        r-cran-shiny \
        r-cran-ssbtools \
        sudo \
    && apt-get purge -y --auto-remove \
    && rm -rf /var/lib/apt/lists/*

# Copy the R script that installs GitHub packages
COPY install_github_r_packages.R /tmp/install_github_r_packages.R

# Use a secret mount so the GITHUB_TOKEN is available only at build time
RUN --mount=type=secret,id=github_pat \
    bash -eux -c "\
      export GITHUB_PAT=$(cat /run/secrets/github_pat) && \
      Rscript /tmp/install_github_r_packages.R \
    "

ENV PATH=/root/.local/bin:$PATH

RUN pipx install poetry && pipx inject poetry poetry-plugin-export \
    && pipx install nox && pipx inject nox nox-poetry

