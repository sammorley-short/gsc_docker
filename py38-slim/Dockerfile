FROM python:3.8-slim-buster

# Install wget and C compilation tools
RUN apt-get update
RUN apt-get install -y wget build-essential

# Install Nauty
WORKDIR /usr/src
RUN wget -O nauty.tar.gz http://pallini.di.uniroma1.it/nauty27r1.tar.gz \
 && tar xvzf nauty.tar.gz \
 && mv nauty27r1 nauty \
 && cd nauty \
 # N.B. -fPIC compile flag needed to avoid compiler error when installing pynauty
 && CC="gcc -fPIC" ./configure \
 && make

# Install PyNauty
WORKDIR /usr/src
RUN wget -O pynauty.tar.gz https://github.com/sammorley-short/pynauty/archive/v1.0.tar.gz \
 && tar xvzf pynauty.tar.gz  \
 && mv pynauty-1.0 pynauty \
 && cd pynauty \
 && ln -s ../nauty nauty \
 && make pynauty \
 && make tests
