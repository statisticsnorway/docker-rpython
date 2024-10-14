# docker-rpython
Repo for creating a docker images containing both python and R, for use in CI and as
dev containers.

## Installed R-packages
The following R-packages with their dependencies are installed in the conatainer image:

From CRAN:
* dplyr
* gausssuppression
* httpgd
* languageserver
* modsem
* shiny
* ssbtools

From GitHub:
* ssb-metodebiblioteket
* ssb-ssb-fellesr

## Usage
```shell
docker pull ghcr.io/statisticsnorway/docker-rpython-base:latest  # Image for use in GitHub Actions
docker pull ghcr.io/statisticsnorway/docker-rpython-dev:latest   # Latest dev-image
```

docker pull 

## Build docker images

### GitHub Action image (base)

From the root of the repo:

```shell
cd docker-base
docker build -t ghcr.io/statisticsnorway/docker-rpython-base:1.0 .
docker push ghcr.io/statisticsnorway/docker-rpython-base:1.0
```

### Dev image

From the root of the repo:

```shell
cd docker-dev
docker build -t ghcr.io/statisticsnorway/docker-rpython-dev:1.0 .
docker push ghcr.io/statisticsnorway/docker-rpython-dev:1.0
```
