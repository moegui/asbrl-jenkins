FROM moegui/jenkins:lts-ws19-1809

ENV JAVA_OPTS=-Djenkins.install.runSetupWizard=false
ARG CASC_JENKINS_CONFIG
ENV CASC_JENKINS_CONFIG=${CASC_JENKINS_CONFIG}

RUN choco install docker-cli -y

RUN "[Net.ServicePointManager]::SecurityProtocol = 'TLS11','TLS12','ssl3'" ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/apache-httpcomponents-client-4-api/latest/apache-httpcomponents-client-4-api.hpi  -OutFile /jenkins_home/plugins/apache-httpcomponents-client-4-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/bouncycastle-api/latest/bouncycastle-api.hpi -OutFile /jenkins_home/plugins/bouncycastle-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/command-launcher/latest/command-launcher.hpi -OutFile /jenkins_home/plugins/command-launcher.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/credentials/latest/credentials.hpi -OutFile /jenkins_home/plugins/credentials.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/display-url-api/latest/display-url-api.hpi  -OutFile /jenkins_home/plugins/display-url-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/git/latest/git.hpi -OutFile /jenkins_home/plugins/git.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/jdk-tool/latest/jdk-tool.hpi -OutFile /jenkins_home/plugins/jdk-tool.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/jsch/latest/jsch.hpi -OutFile /jenkins_home/plugins/jsch.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/junit/latest/junit.hpi -OutFile /jenkins_home/plugins/junit.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/mailer/latest/mailer.hpi -OutFile /jenkins_home/plugins/mailer.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/matrix-project/latest/matrix-project.hpi -OutFile /jenkins_home/plugins/matrix-project.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/scm-api/latest/scm-api.hpi -OutFile /jenkins_home/plugins/scm-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/script-security/latest/script-security.hpi -OutFile /jenkins_home/plugins/script-security.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/ssh-credentials/latest/ssh-credentials.hpi  -OutFile /jenkins_home/plugins/ssh-credentials.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/structs/latest/structs.hpi -OutFile /jenkins_home/plugins/structs.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-api/latest/workflow-api.hpi -OutFile /jenkins_home/plugins/workflow-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-scm-step/latest/workflow-scm-step.hpi -OutFile /jenkins_home/plugins/workflow-scm-step.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-step-api/latest/workflow-step-api.hpi -OutFile /jenkins_home/plugins/workflow-step-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/git-client/latest/git-client.hpi -OutFile /jenkins_home/plugins/git-client.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/job-dsl/latest/job-dsl.hpi -OutFile /jenkins_home/plugins/job-dsl.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/docker-workflow/latest/docker-workflow.hpi -OutFile /jenkins_home/plugins/docker-workflow.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-model-definition/latest/pipeline-model-definition.hpi -OutFile /jenkins_home/plugins/pipeline-model-definition.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-cps/latest/workflow-cps.hpi -OutFile /jenkins_home/plugins/workflow-cps.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/docker-commons/latest/docker-commons.hpi -OutFile /jenkins_home/plugins/docker-commons.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-support/latest/workflow-support.hpi -OutFile /jenkins_home/plugins/workflow-support.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-basic-steps/latest/workflow-basic-steps.hpi -OutFile /jenkins_home/plugins/workflow-basic-steps.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-durable-task-step/latest/workflow-durable-task-step.hpi -OutFile /jenkins_home/plugins/workflow-durable-task-step.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/ace-editor/latest/ace-editor.hpi -OutFile /jenkins_home/plugins/ace-editor.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/jquery-detached/latest/jquery-detached.hpi -OutFile /jenkins_home/plugins/jquery-detached.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/credentials-binding/latest/credentials-binding.hpi -OutFile /jenkins_home/plugins/credentials-binding.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/authentication-tokens/latest/authentication-tokens.hpi -OutFile /jenkins_home/plugins/authentication-tokens.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/durable-task/latest/durable-task.hpi -OutFile /jenkins_home/plugins/durable-task.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/structs/latest/structs.hpi -OutFile /jenkins_home/plugins/structs.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/plain-credentials/latest/plain-credentials.hpi -OutFile /jenkins_home/plugins/plain-credentials.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-cps-global-lib/latest/workflow-cps-global-lib.hpi -OutFile /jenkins_home/plugins/workflow-cps-global-lib.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-multibranch/latest/workflow-multibranch.hpi -OutFile /jenkins_home/plugins/workflow-multibranch.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/trilead-api/latest/trilead-api.hpi -OutFile /jenkins_home/plugins/trilead-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/git-server/latest/git-server.hpi -OutFile /jenkins_home/plugins/git-server.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/cloudbees-folder/latest/cloudbees-folder.hpi -OutFile /jenkins_home/plugins/cloudbees-folder.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/branch-api/latest/branch-api.hpi -OutFile /jenkins_home/plugins/branch-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/workflow-job/latest/workflow-job.hpi -OutFile /jenkins_home/plugins/workflow-job.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-stage-step/latest/pipeline-stage-step.hpi -OutFile /jenkins_home/plugins/pipeline-stage-step.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-stage-tags-metadata/latest/pipeline-stage-tags-metadata.hpi -OutFile /jenkins_home/plugins/pipeline-stage-tags-metadata.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-input-step/latest/pipeline-input-step.hpi -OutFile /jenkins_home/plugins/pipeline-input-step.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-model-declarative-agent/latest/pipeline-model-declarative-agent.hpi -OutFile /jenkins_home/plugins/pipeline-model-declarative-agent.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-model-extensions/latest/pipeline-model-extensions.hpi -OutFile /jenkins_home/plugins/pipeline-model-extensions.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/pipeline-model-api/latest/pipeline-model-api.hpi -OutFile /jenkins_home/plugins/pipeline-model-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/jackson2-api/latest/jackson2-api.hpi -OutFile /jenkins_home/plugins/jackson2-api.jpi ; \
    Invoke-WebRequest -Uri https://updates.jenkins.io/download/plugins/configuration-as-code/latest/configuration-as-code.hpi -OutFile /jenkins_home/plugins/configuration-as-code.jpi ;

COPY jenkins.yml ${CASC_JENKINS_CONFIG}

