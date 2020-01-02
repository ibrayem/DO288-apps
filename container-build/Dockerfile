# Use the httpd-parent image as base
FROM quay.io/redhattraining/httpd-parent

# change the port 8080
EXPOSE 8080

# labels consumed by openshift
LABEL 	io.k8s.description="A basic Apache HTTP Server child image, uses ONBUILD" \
	io.k8s.display-name="Apache HTTP Server" \
	io.openshift.expose-services="8080:http" \
	io.openshift.tags="apache, httpd"

# change web server port 8080
RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf

# Permission to allow container to run on Openshift
RUN 	chgrp -R 0 /var/log/httpd /var/run/httpd && \
	chmod -R g=u /var/log/httpd /var/run/httpd

# Run as non privileged user
USER 1001
