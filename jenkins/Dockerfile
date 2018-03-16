FROM jenkins/jenkins:lts

MAINTAINER Isidro López (islomar@gmail.com)

USER root

RUN apt-get update && apt-get install -y \
  vim \
  curl \
  git

USER jenkins

# get rid of admin password setup
ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false"

# automatically installing all plugins
# (previously extracted running at the Jenkins script page the file plugins.groovy)
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt