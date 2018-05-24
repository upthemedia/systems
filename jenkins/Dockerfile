FROM jenkins/jenkins:lts

MAINTAINER Isidro López (islomar@gmail.com)

USER root

RUN apt-get update && apt-get install -y \
  vim \
  curl \
  git

RUN mkdir /var/log/jenkins
RUN chown -R  jenkins:jenkins /var/log/jenkins

USER jenkins

# get rid of admin password setup
ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false"

# Memory settings to play with in case there are performance problems:
#ENV JAVA_OPTS="-Xmx8192m"
#ENV JENKINS_OPTS="--handlerCountStartup=100 --handlerCountMax=300"

# automatically installing all plugins
# (previously extracted running at the Jenkins script page the file plugins.groovy)
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt