FROM registry.access.redhat.com/ubi8/python-38
USER 0

RUN yum -y install httpd git; yum clean all; systemctl enable httpd.service
COPY  ./mysite/requirements/* /tmp
RUN  pip install --upgrade pip && pip install -r /tmp/base.txt
WORKDIR /opt/app-root/src
RUN git clone https://github.com/huiwangredhat/practice-django.git && \
    cp  ./practice-django/mysite/requirements/* /tmp && \
    pip install --upgrade pip && pip install -r /tmp/base.txt --use-pep517 && \
    mkdir -p  /var/log/mysite/ && \
    mkdir /var/mysite && \
    sed -i -e 's/^Listen 80/Listen 8080/' /etc/httpd/conf/httpd.conf && \
    sed -i -e "s/^User apache/User default/" /etc/httpd/conf/httpd.conf && \
    sed -i -e "s/^Group apache/Group root/" /etc/httpd/conf/httpd.conf && \
    echo "LoadModule mpm_event_module modules/mod_mpm_event.so" > /etc/httpd/conf.modules.d/00-mpm.conf && \
    chmod a+rwX -R /run/httpd/ /var/log/httpd/ /var/log/mysite/ /var/cache/ \
         /etc/passwd  /var/mysite && \
    mkdir -p /var/mysite/static && \
    ./practice-django/mysite/manage.py collectstatic --noinput --clear --link

EXPOSE 8080/tcp
CMD ["/usr/sbin/init"]
USER 1001
