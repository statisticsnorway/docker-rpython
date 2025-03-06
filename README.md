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

## Releases

The docker images are published as GitHub Packages on
[this page](https://github.com/statisticsnorway/docker-rpython/pkgs/container/docker-rpython-base). 

## Usage

```shell
docker pull ghcr.io/statisticsnorway/docker-rpython-base:latest  # Image for use in GitHub Actions
docker pull ghcr.io/statisticsnorway/docker-rpython-dev:latest   # Latest dev-image
```

## Build docker images

### Automatically

Both docker images are built and published when a tag starting with `v` is pushed
to the repo. Example:

```shell
git tag  # List existing tags, pick the next one
git tag -a v1.0.3 -m"Tagging docker image"  # create new tag
git push --tags
```

### Manually

#### GitHub Action image (base)

From the root of the repo:

```shell
cd base
docker build -t ghcr.io/statisticsnorway/docker-rpython-base:1.0 .
docker push ghcr.io/statisticsnorway/docker-rpython-base:1.0
```

#### Dev image

From the root of the repo:

```shell
cd dev
docker build -t ghcr.io/statisticsnorway/docker-rpython-dev:1.0 .
docker push ghcr.io/statisticsnorway/docker-rpython-dev:1.0
```

### Authenticate with GitHub Container Registry

Your PATH must have the `read:packages` scope.

```shell
export CR_PAT=<YourPAT>
echo $CR_PAT | docker login ghcr.io -u USERNAME --password-stdin
```
