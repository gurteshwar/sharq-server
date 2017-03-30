Sharq-Server Dev-Setup with Docker
==================================

## Pre-requisites

* Your development system needs to have Docker
  installed. [For Ubuntu](http://docs.docker.com/installation/ubuntulinux/)
  [For Mac](http://docs.docker.com/installation/mac/) [Others]
  (http://docs.docker.com/installation/)
* Check out this repository to a local directory - let's say the
  directory is called `$CODE`. Let it be:
  $GOPATH/src/github.com/plivo/sharq-server

## Suggested workflow for development

* Before making changes to the code, build the container with:

```bash
cd $CODE
sudo docker build -f Dockerfile.sharq -t sharq-server .
```

* Now build the Redis container:

```bash
cd $CODE
docker build -t sharq/redis .
```

* Now run the Redis container:

```bash
docker run --name redis -d sharq/redis
```

* Now run the callback container for the test cases

```bash
docker run --rm --link redis sharq-server 
```

The configuration file used in the run is from `$CODE/config.json`.

For advanced usage, the options for the `docker run` command are
useful. [Doc](https://docs.docker.com/reference/run/)

