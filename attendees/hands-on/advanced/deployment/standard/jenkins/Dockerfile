FROM jenkins
COPY jenkins/plugins.txt /usr/share/jenkins/ref/plugins.txt
USER root

RUN curl -fsSLO https://get.docker.com/builds/Linux/x86_64/docker-1.11.2.tgz && tar --strip-components=1 -xvzf docker-1.11.2.tgz -C /usr/local/bin

RUN /usr/local/bin/plugins.sh /usr/share/jenkins/ref/plugins.txt
RUN echo 2.0 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state
RUN mkdir /root/.ssh
COPY jenkins/seed-job.groovy /usr/share/jenkins/ref/init.groovy.d/
COPY jenkins/init.groovy     /usr/share/jenkins/ref/init.groovy
