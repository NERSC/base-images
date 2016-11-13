FROM centos:7
MAINTAINER Shane Canon <scanon@lbl.gov>

RUN yum -y update 

RUN yum -y install gcc make gcc-gfortran gcc-c++ wget curl

RUN \
    cd /usr/local/src/ && \
    wget http://www.mpich.org/static/downloads/3.2/mpich-3.2.tar.gz && \
    tar xf mpich-3.2.tar.gz && \
    rm mpich-3.2.tar.gz && \
    cd mpich-3.2 && \
    ./configure && \
    make && make install && \
    cd /usr/local/src && \
    rm -rf mpich-3.2


RUN \
    yum install -y python-devel && \
    wget https://bitbucket.org/mpi4py/mpi4py/downloads/mpi4py-2.0.0.tar.gz && \
    tar xzf mpi4py-2.0.0.tar.gz  && \
    rm mpi4py-2.0.0.tar.gz && \
    cd mpi4py-2.0.0 && \
    python setup.py  build && \
    python setup.py  install && \
    cp -a demo/ / && \
    cd .. && rm -rf mpi4py-2.0.0

ENV PATH=/usr/bin:/usr/local/bin:/bin:/app
