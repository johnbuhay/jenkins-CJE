FROM jenkins:latest

# Install supporting software
USER root
ENV DEBIAN_FRONTEND=noninteractive LANG=C.UTF-8 TERM=xterm  \
    BASE_PACKAGES="ca-certificates curl wget vim less dnsutils tcpdump pypy git build-essential"

RUN env | sort && apt-get -yq update && apt-get install -y --no-install-recommends apt-utils locales &&  \
    apt-get -yq install --no-install-recommends ${BASE_PACKAGES} &&  \
    apt-get clean &&  \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* &&  \
    ln -s /usr/bin/pypy /usr/local/bin/python

# Install plugins and config 
USER jenkins
COPY plugins.txt /usr/share/jenkins/plugins.txt


RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt
