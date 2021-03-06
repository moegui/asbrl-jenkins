FROM jenkins/jenkins:lts

ARG ROOT_PASS
ARG ROOT_USER
ARG JENKINS_HOME
ARG HTTP_PORT
ARG AGENT_PORT
ARG EXECUTORS
ARG GIT_SEED
ARG CASC_JENKINS_CONFIG
ARG JENKINS_URL
ARG JENKINS_EMAIL
ARG JENKINS_SSH_KEY
ARG JENKINS_SSH_NAME
ARG JENKINS_SEEDER
ARG JENKINS_OPTS
ARG DOCKER_USER_NAME
ARG DOCKER_USER_PASS

ENV CASC_JENKINS_CONFIG=${CASC_JENKINS_CONFIG} HTTP_PORT=${HTTP_PORT} GIT_SEED=${GIT_SEED} JENKINS_EMAIL=${JENKINS_EMAIL}
ENV ROOT_USER=${ROOT_USER} ROOT_PASS=${ROOT_PASS} AGENT_PORT=${AGENT_PORT} EXECUTORS=${EXECUTORS} JENKINS_URL=${JENKINS_URL}
ENV JENKINS_SSH_KEY=${JENKINS_SSH_KEY} JENKINS_SSH_NAME=${JENKINS_SSH_NAME} JENKINS_SEEDER=${JENKINS_SEEDER} JENKINS_OPTS=${JENKINS_OPTS}
ENV DOCKER_USER_NAME=${DOCKER_USER_NAME} DOCKER_USER_PASS={DOCKER_USER_PASS}

COPY jenkins.yml ${CASC_JENKINS_CONFIG}

RUN install-plugins.sh git \
                       pipeline-model-definition \
                       configuration-as-code \
                       docker-workflow \
                       job-dsl

EXPOSE ${HTTP_PORT}/tcp ${AGENT_PORT}/tcp

USER root

RUN apt-get update && \
    apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    rsync \
    software-properties-common -y

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -

RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable" && \
   apt-get update && \
   apt-get install docker-ce-cli -y 

USER jenkins