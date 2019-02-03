FROM debian:jessie

MAINTAINER Vlad Umanskyi <vladumanskyi@gmail.com>

RUN apt-get update && apt-get install -y \
    nginx

ADD ./conf/nginx.conf /etc/nginx/
ADD ./conf/website.conf /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/website.conf /etc/nginx/sites-enabled/website \
&& rm /etc/nginx/sites-enabled/default

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
