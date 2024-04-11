# FROM amazonlinux:2.0.20191016.0
# RUN yum install -y python37 && \
#     yum install -y python3-pip && \
#     yum install -y zip && \
#     yum clean all
# RUN python3.7 -m pip install --upgrade pip && \
#     python3.7 -m pip install virtualenv


# FROM amazonlinux:latest
# RUN yum update -y
# RUN yum install -y \
# python3-pip \
# zip \
# RUN yum -y clean all
# RUN python3.9 -m pip install --upgrade pip

FROM amazonlinux:2.0.20191016.0
RUN yum -y groupinstall "Development Tools" && \
    yum -y install sqlite-devel openssl-devel bzip2-devel libffi-devel && \
    yum -y install -y zip && \
    yum -y install wget && \
    wget https://www.python.org/ftp/python/3.9.10/Python-3.9.10.tgz && \
    tar xvf Python-3.9.10.tgz && \
    cd Python-*/ &&\
    ./configure --enable-optimizations && \
    make altinstall && \
    python3.9 -m pip install --upgrade pip && \
    python3.9 -m pip install virtualenv