
FROM ibm-java:latest

MAINTAINER Niklaus Hirt <nikh@ch.ibm.com>

# This build expects the ibm-ucd-dev.zip to be in the current directory
# as well as an install.properties file.
ADD ibm-ucd-dev.zip /tmp/ibm-ucd-server.zip
ADD install.properties /tmp/install.properties



# install the UCD Server and remove the install files.
RUN apt-get update -qq && \
	apt-get --no-install-recommends install -qq curl unzip > /dev/null \
  	&& rm -rf /var/lib/apt/lists/* && \
	cd /tmp && \
	unzip -q ibm-ucd-server.zip && \
	cp -f /tmp/install.properties /tmp/ibm-ucd-install/install.properties && \
	sh /tmp/ibm-ucd-install/install-server.sh && \
	rm -rf /tmp/ibm-ucd-install && \
	rm -rf /tmp/ibm-ucd-server.zip


# HTTP, HTTPS, JMS
EXPOSE 8080
EXPOSE 8443
EXPOSE 7918


# TODO - replace this with install.dir from install.properties - but how?
# For now, override this with --entrypoint=$INSTALL_DIR/bin/server if needed
ENTRYPOINT ["/opt/ibm-ucd/server/bin/server"]
CMD ["run"]
