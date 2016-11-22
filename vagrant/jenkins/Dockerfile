FROM jenkins:alpine

USER root
# install sudo and curl
RUN apk add --update bash \
      && apk add sudo curl busybox docker \
      && rm -rf /var/cache/apk/*
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

# getting the docker-cli
# --- Attention: docker.sock needs to be mounted as volume in docker-compose.yml
# see: https://issues.jenkins-ci.org/browse/JENKINS-35025
# see: https://get.docker.com/builds/
# see: https://wiki.jenkins-ci.org/display/JENKINS/CloudBees+Docker+Custom+Build+Environment+Plugin#CloudBeesDockerCustomBuildEnvironmentPlugin-DockerinDocker
#RUN curl -sSL -O https://get.docker.com/builds/Linux/x86_64/docker-latest.tgz && tar -xvzf docker-latest.tgz
#RUN mv docker/* /usr/bin/
#RUN apk add docker-1.12.3

#RUN adduser -G docker jenkins
RUN mkdir /var/run/docker.socket
RUN chmod a+r,a+w /var/run/docker.socket

USER jenkins

# install specific list of plugins. see: https://github.com/jenkinsci/docker#preinstalling-plugins
#COPY plugins.txt /var/jenkins_home/plugins.txt
#RUN /usr/local/bin/plugins.sh /var/jenkins_home/plugins.txt

# Jenkins settings
#COPY config/config.xml /usr/share/jenkins/ref/config.xml
#COPY config/scriptApproval.xml /usr/share/jenkins/ref/scriptApproval.xml

# Jenkins Settings, i.e. Maven, Groovy, ...
#COPY config/hudson.tasks.Maven.xml /usr/share/jenkins/ref/hudson.tasks.Maven.xml
#COPY config/hudson.plugins.groovy.Groovy.xml /usr/share/jenkins/ref/hudson.plugins.groovy.Groovy.xml
#COPY config/maven-global-settings-files.xml /usr/share/jenkins/ref/maven-global-settings-files.xml

# SSH Keys & Credentials
#COPY config/credentials.xml /usr/share/jenkins/ref/credentials.xml
#COPY config/ssh-keys/cd-demo /usr/share/jenkins/ref/.ssh/id_rsa
#COPY config/ssh-keys/cd-demo.pub /usr/share/jenkins/ref/.ssh/id_rsa.pub

# tell Jenkins that no banner prompt for pipeline plugins is needed
# see: https://github.com/jenkinsci/docker#preinstalling-plugins
#RUN echo 2.0 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state

