FROM <base image>

MAINTAINER username <username@example.com>

ENV PORT <port>

RUN <provide yum commands in a single line>

RUN sed -ri -e "/^Listen 80/c\Listen ${PORT}" /etc/httpd/conf/httpd.conf && \
    chown -R apache:apache /etc/httpd/logs/ && \
    chown -R apache:apache /run/httpd/

USER apache

# Expose the custom port that you provided in the ENV var

# Copy all files under src/ folder to Apache DocumentRoot (/var/www/html) 

# Start Apache in the foreground
