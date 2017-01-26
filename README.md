# 11-364 Docker Image

A docker image to build containers for 11-364: Introduction to Deep Learning @ CMU. The image is built from
Ubuntu 14.04 and contains the following packages, among others.

* [Tensorflow](https://www.tensorflow.org/)
* [Theano](http://deeplearning.net/software/theano/)
* [Keras](http://keras.io/)
* [Numpy](http://www.numpy.org/)
* [SciPy](https://www.scipy.org/)
* [Pandas](http://pandas.pydata.org/)
* [Scikit Learn](http://scikit-learn.org/)
* [Matplotlib](http://matplotlib.org/)
* [Neuralpy](https://jon--lee.github.io/neuralpy/)

## Setup

### Prerequisites
Install Docker by following the installation guide: [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)

### Obtaining the image
You have 2 options to obtain the Docker image
#### Option 1: Download the image from Docker Hub
Docker Hub is a cloud based repository of pre-built images. You can download the image directly from here, which is WAY faster than building it locally. Here is the `11364-docker`: [https://hub.docker.com/r/rbrigden/11364-docker/](https://hub.docker.com/r/rbrigden/11364-docker/).

```bash
$ docker pull rbrigden/11364-docker
$ docker tag rbrigden/11364-docker 11364
```

Note: The second command will rename the image locally to 11364. Therefore,
we will assume from hereon that the name of the image is 11364.

#### Option 2: Build the image locally
Alternatively, you can build the images locally. Note that this could take 20-30 minutes to install all
of the libraries from scratch.

```bash
$ git clone https://github.com/rbrigden/11364-docker.git
$ cd 11364-docker
$ docker build -t 11364 .
```

## Running the container

```bash
$ docker run -dit rbrigden/11364-docker
$ docker attach
```

## Working with your local files

You will probably want to write code locally that will be run in the container (which has
its own filesystem). The good news is that there is an easy way to share files between
the container and your local machine. We can achieve this by mounting a shared volume
between the container and a local directory of your choice. Preferably this is the directory
for the project utilizing the container's packages.

If you want to create a volume that mounts to /path/to/host/dir/ and /path/to/container/dir, spin
up the container as follows:

```bash
$ docker run -dit -v /path/to/host/dir/:/root/path/to/container/dir rbrigden/11364-docker
$ docker attach
```

All changes that you make in the container or the host will be immediately
visible to the other in the shared volume. Changes are persistent, so deleting the
container will not affect the state of the shared directory.

Note 1: You should add the base path of "/root/" for the shared volume in the container.
This will make it so that the directory is accessible as soon as you attach the container.

Note 2: The specified paths must be absolute, not relative.
