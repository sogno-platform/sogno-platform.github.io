# SOGNO Docs Website Development Container

## Requirements

Make sure all submodules are checked out:

```bash
git submodule update --init --recursive
```

## Build Image

The custom docker image including Hugo and all dependencies needs to be build locally:

```bash
docker build . -t sogno-hugo
```

## Start Container

Once the image is ready, we can bind mount the current folder (assuming this website repo) into the container and expose port 1313 of the development server.
On startup, the container will install additional packages and finally launch the Hugo development server.
It will automatically detect changes in the local website files and rebuild the website immediately.

```bash
docker run -v $PWD:/website -p 1313:1313 -it sogno-hugo 
```

The website will be available under [http://localhost:1313](http://localhost:1313)


## TL;DR

```bash
git submodule update --init --recursive
docker build . -t sogno-hugo
docker run -v $PWD:/website -p 1313:1313 -it sogno-hugo
```
