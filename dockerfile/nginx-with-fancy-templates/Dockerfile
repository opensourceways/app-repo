FROM ubuntu:xenial
MAINTAINER tommylike <tommylikehu@gmail.com>
# Set env
USER root
ENV USER root

RUN apt -y update \
    && apt install -y wget \
    && apt install -y git \
    && apt install -y make build-essential libpcre3 libpcre3-dev openssl libssl-dev software-properties-common openssh-server tzdata\
    && rm -rf /var/lib/{apt,dpkg,cache,log}/

# prepare nginx
RUN wget http://nginx.org/download/nginx-1.20.0.tar.gz \
    && tar -xvf nginx-1.20.0.tar.gz && rm nginx-1.20.0.tar.gz

# prepare nginx fancyindex
RUN git clone https://github.com/aperezdc/ngx-fancyindex.git ngx-fancyindex

RUN cd nginx-1.20.0 \
    && ./configure --prefix=/etc/nginx/ --add-module=../ngx-fancyindex \
    && make && make install \
    && cd ../ && rm -rf nginx-1.20.0  && rm -rf ngx-fancyindex\
    && mkdir -p /var/log/nginx

# Copy templates into /etc/nginx/conf/static
ADD ./fancySource/openEuler /etc/nginx/conf/static/fancySource
ENV PATH="/etc/nginx/sbin:${PATH}"
ENTRYPOINT ["nginx", "-g", "daemon off;"]
