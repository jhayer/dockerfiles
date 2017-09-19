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
    make all && \
    cd scripts && \
    chmod +x *

# install minimap
RUN git clone https://github.com/lh3/minimap && \
    cd minimap && \
    make

# install samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.5/samtools-1.5.tar.bz2 && \
    tar xf samtools-1.5.tar.bz2 && \
    cd samtools-1.5 && \
    make && \
    make install && \
    cd .. && \
    rm -rf samtools-1.5

# install parallel
RUN apt-get install parallel

ENV PATH /minimap:/nanopolish:/nanopolish/scripts:$PATH
