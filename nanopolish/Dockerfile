FROM hadrieng/docker_base

MAINTAINER Juliette Hayer <juliette.hayer@gmail.com>

# first install pip
RUN wget https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py
# install numpy and biopython
RUN pip install numpy && \
    pip install biopython

# install nanopolish
RUN git clone --recursive https://github.com/jts/nanopolish.git && \
    cd nanopolish/ && \
    make all \
    cd scripts && \
    chmod +x *

ENV PATH /nanopolish:/nanopolish/scripts:$PATH
