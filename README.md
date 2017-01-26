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
1. Install Docker following the installation guide: [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)

### Obtaining the Docker image
You have 2 options to obtain the Docker image
#### Option 1: Download the image from Docker Hub
Docker Hub is a cloud based repository of pre-built images. You can download the image directly from here, which is WAY faster than building it locally. Here is the `11364-docker`: [https://hub.docker.com/r/floydhub/dl-docker/](https://hub.docker.com/r/floydhub/dl-docker/).

```bash
docker pull floydhub/dl-docker:cpu
```

#### Option 2: Build the image locally
Alternatively, you can build the images locally. Note that this could take 20-30 minutes to install all
of the libraries from scratch.

```bash
git clone https://github.com/saiprashanths/dl-docker.git
cd dl-docker
```

## Running the container


## Working with your local files

You will probably want to write code locally that will be run in the container (which has
its own filesystem). The good news is that there is an easy way to share files between
the container and your local machine. We can achieve this by mounting a shared volume
between the container and
