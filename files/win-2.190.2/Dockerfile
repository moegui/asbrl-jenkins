FROM openjdk:11.0.5-windowsservercore-1809

ARG JENKINS_VERSION
ENV JENKINS_VERSION ${JENKINS_VERSION:-2.190.2}
ARG JENKINS_URL=https://repo.jenkins-ci.org/public/org/jenkins-ci/main/jenkins-war/${JENKINS_VERSION}/jenkins-war-${JENKINS_VERSION}.war
ENV HOME /jenkins_home
ARG JENKINS_HOME=\jenkins_home
ENV JENKINS_HOME $JENKINS_HOME
ARG http_port=8080
ARG agent_port=50000
ENV JENKINS_SLAVE_AGENT_PORT ${agent_port}
ENV JAVA_OPTS=-Djenkins.install.runSetupWizard=false
ARG CASC_JENKINS_CONFIG
ENV CASC_JENKINS_CONFIG=${CASC_JENKINS_CONFIG}

RUN mkdir \jenkins_home
RUN mkdir \jenkins_home\workspace
RUN mkdir \jenkins_home\plugins

RUN "[Net.ServicePointManager]::SecurityProtocol = 'TLS11','TLS12','ssl3'" ; \
    Invoke-WebRequest -Uri ${env:JENKINS_URL} -OutFile \jenkins_home\jenkins.war ;

RUN Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

RUN choco install git -y

RUN "[Net.ServicePointManager]::SecurityProtocol = 'TLS11','TLS12','ssl3'" ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/apache-httpcomponents-client-4-api/4.5.5-3.0/apache-httpcomponents-client-4-api.hpi  -OutFile /jenkins_home/plugins/apache-httpcomponents-client-4-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/bouncycastle-api/2.17/bouncycastle-api.hpi -OutFile /jenkins_home/plugins/bouncycastle-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/command-launcher/1.3/command-launcher.hpi -OutFile /jenkins_home/plugins/command-launcher.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/credentials/2.3.0/credentials.hpi -OutFile /jenkins_home/plugins/credentials.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/display-url-api/2.3.0/display-url-api.hpi  -OutFile /jenkins_home/plugins/display-url-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/git/3.9.3/git.hpi -OutFile /jenkins_home/plugins/git.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/jdk-tool/1.2/jdk-tool.hpi -OutFile /jenkins_home/plugins/jdk-tool.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/jsch/0.1.55/jsch.hpi -OutFile /jenkins_home/plugins/jsch.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/junit/1.27/junit.hpi -OutFile /jenkins_home/plugins/junit.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/mailer/1.23/mailer.hpi -OutFile /jenkins_home/plugins/mailer.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/matrix-project/1.14/matrix-project.hpi -OutFile /jenkins_home/plugins/matrix-project.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/scm-api/2.6.3/scm-api.hpi -OutFile /jenkins_home/plugins/scm-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/script-security/1.66/script-security.hpi -OutFile /jenkins_home/plugins/script-security.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/ssh-credentials/1.18/ssh-credentials.hpi  -OutFile /jenkins_home/plugins/ssh-credentials.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/structs/1.17/structs.hpi -OutFile /jenkins_home/plugins/structs.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-api/2.37/workflow-api.hpi -OutFile /jenkins_home/plugins/workflow-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-scm-step/2.9/workflow-scm-step.hpi -OutFile /jenkins_home/plugins/workflow-scm-step.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-step-api/2.20/workflow-step-api.hpi -OutFile /jenkins_home/plugins/workflow-step-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/git-client/2.7.6/git-client.hpi -OutFile /jenkins_home/plugins/git-client.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/job-dsl/1.76/job-dsl.hpi -OutFile /jenkins_home/plugins/job-dsl.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/docker-workflow/1.21/docker-workflow.hpi -OutFile /jenkins_home/plugins/docker-workflow.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-model-definition/1.4.0/pipeline-model-definition.hpi -OutFile /jenkins_home/plugins/pipeline-model-definition.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-cps/2.75/workflow-cps.hpi -OutFile /jenkins_home/plugins/workflow-cps.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/docker-commons/1.15/docker-commons.hpi -OutFile /jenkins_home/plugins/docker-commons.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-support/3.3/workflow-support.hpi -OutFile /jenkins_home/plugins/workflow-support.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-basic-steps/2.18/workflow-basic-steps.hpi -OutFile /jenkins_home/plugins/workflow-basic-steps.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-durable-task-step/2.35/workflow-durable-task-step.hpi -OutFile /jenkins_home/plugins/workflow-durable-task-step.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/ace-editor/1.1/ace-editor.hpi -OutFile /jenkins_home/plugins/ace-editor.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/jquery-detached/1.2.1/jquery-detached.hpi -OutFile /jenkins_home/plugins/jquery-detached.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/credentials-binding/1.20/credentials-binding.hpi -OutFile /jenkins_home/plugins/credentials-binding.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/authentication-tokens/1.3/authentication-tokens.hpi -OutFile /jenkins_home/plugins/authentication-tokens.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/durable-task/1.33/durable-task.hpi -OutFile /jenkins_home/plugins/durable-task.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/structs/1.20/structs.hpi -OutFile /jenkins_home/plugins/structs.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/plain-credentials/1.5/plain-credentials.hpi -OutFile /jenkins_home/plugins/plain-credentials.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-cps-global-lib/2.15/workflow-cps-global-lib.hpi -OutFile /jenkins_home/plugins/workflow-cps-global-lib.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-multibranch/2.21/workflow-multibranch.hpi -OutFile /jenkins_home/plugins/workflow-multibranch.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/trilead-api/1.0.5/trilead-api.hpi -OutFile /jenkins_home/plugins/trilead-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/git-server/1.8/git-server.hpi -OutFile /jenkins_home/plugins/git-server.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/cloudbees-folder/6.9/cloudbees-folder.hpi -OutFile /jenkins_home/plugins/cloudbees-folder.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/branch-api/2.5.4/branch-api.hpi -OutFile /jenkins_home/plugins/branch-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-job/2.36/workflow-job.hpi -OutFile /jenkins_home/plugins/workflow-job.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-stage-step/2.3/pipeline-stage-step.hpi -OutFile /jenkins_home/plugins/pipeline-stage-step.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-stage-tags-metadata/1.4.0/pipeline-stage-tags-metadata.hpi -OutFile /jenkins_home/plugins/pipeline-stage-tags-metadata.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-input-step/2.11/pipeline-input-step.hpi -OutFile /jenkins_home/plugins/pipeline-input-step.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-model-declarative-agent/1.1.1/pipeline-model-declarative-agent.hpi -OutFile /jenkins_home/plugins/pipeline-model-declarative-agent.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-model-extensions/1.4.0/pipeline-model-extensions.hpi -OutFile /jenkins_home/plugins/pipeline-model-extensions.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/configuration-as-code/1.32/configuration-as-code.hpi -OutFile /jenkins_home/plugins/configuration-as-code.jpi ;
COPY jenkins.yml ${CASC_JENKINS_CONFIG}

EXPOSE ${http_port}
EXPOSE ${agent_port}

CMD java -jar C:\\jenkins_home\\jenkins.war ${JAVA_OPTS}

