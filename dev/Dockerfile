FROM ghcr.io/statisticsnorway/docker-rpython-base:1.0

LABEL org.opencontainers.image.source=https://github.com/statisticsnorway/docker-rpython
LABEL org.opencontainers.image.description="Container for running both python and R."
LABEL org.opencontainers.image.licenses=MIT

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        libcairo2-dev \
        libcurl4-openssl-dev \
        libfontconfig1-dev \
        libfreetype6-dev \
        libfribidi-dev \
        libharfbuzz-dev \
        libjpeg-dev \
        libpango1.0-dev \
        libpng-dev \
        libssl-dev \
        libtiff-dev \
        libxml2-dev \
        python-is-python3 \
        python3 \
        python3-dev \
    && apt-get purge -y --auto-remove \
    && rm -rf /var/lib/apt/lists/*
