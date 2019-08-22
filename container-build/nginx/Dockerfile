FROM centos:centos7.6.1810

MAINTAINER Rosario Cafaro <cafaro.rosario@gmail.com>

RUN yum update -y && \
    yum install -y epel-release

RUN yum install -y nginx

COPY ./container-build/nginx/nginx.conf /etc/nginx/nginx.conf
COPY ./container-build/nginx/app.conf /etc/nginx/conf.d/app.conf

RUN yum clean all

CMD nginx
