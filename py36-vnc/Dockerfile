FROM x11vnc/docker-desktop
USER ubuntu

# Install development packages for C++
RUN sudo apt-get update
RUN sudo apt-get install -y wget build-essential

# Install Nauty
WORKDIR /home/ubuntu
RUN wget -O nauty.tar.gz http://pallini.di.uniroma1.it/nauty27r1.tar.gz \
 && tar xvzf nauty.tar.gz \
 && rm nauty.tar.gz \
 && mv nauty27r1 nauty \
 && cd nauty \
 # N.B. -fPIC compile flag needed to avoid compiler error when installing pynauty
 && CC="gcc -fPIC" ./configure \
 && make

# Install development packages for Python 3
RUN sudo apt-get update
RUN sudo apt-get install -y python-dev

# Install PyNauty
WORKDIR /home/ubuntu
RUN wget -O pynauty.tar.gz https://github.com/sammorley-short/pynauty/archive/v1.0.tar.gz \
 && tar xvzf pynauty.tar.gz  \
 && rm pynauty.tar.gz \
 && mv pynauty-1.0 pynauty \
 && cd pynauty \
 && mv ../nauty nauty \
 && make pynauty \
 && make tests 

# Install Python 3 venv
RUN sudo apt-get update
RUN sudo apt-get install -y python3-venv python3-dev

# Create Python 3 venv and install PyNauty there
WORKDIR /home/ubuntu
RUN python3 -m venv venv
RUN . venv/bin/activate \
 && cd pynauty \
 && make virtenv-ins

