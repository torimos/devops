CICD

Job - "{PROJECT_NAME} Build":
  This job will be used to build project from git branch name specified in string parameter of job, for instance "release/1.5.2"
  This job will tag build and artifacts with name of branch specified in parameter of job, so for example:
    - build name will be "#{BUILD_NUMBER} (release/1.5.2)"
    - artifact name will be "{PROJECT_NAME} release/1.5.2"

Job - "{PROJECT_NAME} Deploy":
  This job will be used to deploy pre-built project from artifact name and target environment name for deployment, specified in string parameters of job.

============================================================================

Release build preparation
RM triggers build with 4release options turned-on.
Such build will make build and test to ensure that it is stable and will create release branch with specified name, send email with release details and notes :) 


============================================================================
Pipeline - "{PROJECT_NAME} Release":
  This pipline will use branch name (in parameters) to trigger build and to start deployment to QA.
  All further deployments will require approval:
  Build > QA > Approve? > UAT > Approve? > PROD

