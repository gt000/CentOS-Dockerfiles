FROM centos:7
MAINTAINER The CentOS Project <cloud-ops@centos.org>
LABEL Vendor="CentOS" \
      License=GPLv2 \
      Version=2.4.6-40


RUN yum -y --setopt=tsflags=nodocs update && \
    yum -y --setopt=tsflags=nodocs install httpd && \
    yum clean all

EXPOSE 80

# Simple startup script to avoid some issues observed with container restart
ADD run-httpd.sh /run-httpd.sh
RUN chgrp -R 0 /some/directory
RUN chmod -R g+rw /some/directory
RUN find /some/directory -type d -exec chmod g+x {} +
RUN chmod -v +x /run-httpd.sh

CMD ["/run-httpd.sh"]
