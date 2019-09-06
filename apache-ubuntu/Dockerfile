# Container used to test Content Management feature
#
# VERSION               1.0.0

FROM ubuntu
MAINTAINER Michele Bologna <michele.bologna@suse.com>

ARG repo
ARG cert

RUN echo "$cert" > /tmp/cert.pem
#RUN update-ca-certificates
RUN echo "$repo" > /tmp/repo

ADD add_packages.sh /root/add_packages.sh
RUN /root/add_packages.sh

ADD pub.conf /etc/apache2/conf-available/pub.conf
RUN ln -s /etc/apache2/conf-available/pub.conf /etc/apache2/conf-enabled/pub.conf && mkdir -p /srv/www/htdocs/pub/
ADD index.html /srv/www/htdocs/pub/index.html

CMD ["/usr/sbin/apachectl", "-DFOREGROUND"]


