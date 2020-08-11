pipeline {
  agent {
    docker {
      image "bryandollery/terraform-packer-aws-alpine"
      args "-u root"
    }
  }
  environment {
    CREDS = credentials('aws-creds')
    AWS_ACCESS_KEY_ID = "$CREDS_USR"
    AWS_SECRET_ACCESS_KEY = "$CREDS_PSW"
    OWNER = 'bryan'
    PROJECT_NAME = 'web-server'
    AWS_PROFILE="kh-labs"
    TF_NAMESPACE="jenkins-lab-2"
  }
  stages {
      stage("init") {
          make init
      }
      stage("plan") {
          make plan
      }
      stage("apply") {
          make apply
      }
  }
}
