FROM jenkins/jenkins:lts-jdk11

USER root

RUN apt-get update && \
    curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose && \
    curl https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.7.0.2747-linux.zip -O && \
    unzip sonar-scanner-cli-4.7.0.2747-linux.zip && \
    apt install vim apt-transport-https  ca-certificates curl gnupg-agent software-properties-common -y && \
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - && \
    apt-key fingerprint 0EBFCD88 && \
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && \
    apt-get update && apt-get install docker-ce -y && apt-get clean 