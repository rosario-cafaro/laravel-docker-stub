FROM centos:centos7.6.1810

MAINTAINER Rosario Cafaro <cafaro.rosario@gmail.com>

RUN yum update -y && \
    yum install -y epel-release

RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm && \
    yum -y --enablerepo=remi-php73 install php && \
    yum -y --enablerepo=remi-php73 install php-fpm php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt php-cli php-dba php-gd php-intl php-mbstring php-mysql php-pdo php-pecl-apcu php-pecl-imagick php73-php-bcmath

RUN useradd -M -d /opt/app -s /bin/false nginx

RUN mkdir -p /run/php-fpm && \
    chown nginx:nginx /run/php-fpm

RUN mkdir -p /var/lib/php/session && \
    chown nginx:nginx /var/lib/php/session

COPY ./container-build/php-fpm/php-fpm.conf /etc/php-fpm.conf
COPY ./container-build/php-fpm/www.conf /etc/php-fpm.d/www.conf
COPY ./container-build/php-fpm/php.ini /etc/php.ini

RUN yum clean all

CMD php-fpm
