FROM jenkins/jenkins:2.346.1-jdk11

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
USER root
RUN apt-get update && apt-get install -y apt-transport-https \
       ca-certificates curl gnupg2 \
       software-properties-common
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN apt-key fingerprint 0EBFCD88
RUN add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/debian \
       $(lsb_release -cs) stable"
RUN apt-get update && apt-get install -y docker-ce-cli
RUN jenkins-plugin-cli --plugins \
    "saferestart:latest kubernetes:latest blueocean:1.25.5 docker-workflow:1.28 configuration-as-code:latest matrix-auth:latest authorize-project:latest logstash:latest"