# PyNauty docker images

The following docker images are made available to support the development of the [pynauty](https://github.com/sammorley-short/pynauty) package.
These can also be found on Docker Hub [here](https://hub.docker.com/r/sammorleyshort/pynauty/tags).

The following images are included:

* `py27`: uses the Ubuntu 16.04 base image
* `py27-slim`: uses the official Python 2.7 slim Debian Buster base image.
* `py36-vnc`: uses the `x11vnc/docker-desktop` base image, which allows users to use VNC to connect to a lightweight LXDE desktop running on Ubuntu 18.04. This is provided for users who prefer to develop using desktop applications rather than through command-line tools.
* `py38-slim`: uses the official Python 3.8 slim Debian Buster base image.
