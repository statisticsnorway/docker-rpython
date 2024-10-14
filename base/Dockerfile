FROM rocker/r2u:24.04

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
        python3-poetry \
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

RUN R -e "remotes::install_github(c(\
   'statisticsnorway/ssb-metodebiblioteket', \
   'statisticsnorway/ssb-fellesr' \
   ))"   

RUN pipx ensurepath && pipx install nox && pipx inject nox nox-poetry

