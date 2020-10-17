FROM ubi7/ubi:7.7
MAINTAINER Tim Robert <trobert@tmail.com>
LABEL description="This is a custom image for Ubi"
RUN yum install -y httpd && \
    yum clean all
RUN echo "Hello! This is created from customized Dockerfile" > /usr/share/httpd/noindex/index.html
EXPOSE 80
ENTRYPOINT ["httpd", "-D", "FOREGROUND"]
