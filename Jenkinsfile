pipeline {
  agent any

  environment {
    AWS_ACCESS_KEY = credentials('aws-access-key-id')
    AWS_SECRET_KEY = credentials('aws-secret-access-key')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/yourusername/terraform-ec2-deploy.git'
      }
    }

    stage('Init') {
      steps {
        sh 'terraform init'
      }
    }

    stage('Plan') {
      steps {
        sh 'terraform plan -var="access_key=${AWS_ACCESS_KEY}" -var="secret_key=${AWS_SECRET_KEY}"'
      }
    }

    stage('Apply') {
      steps {
        sh 'terraform apply -auto-approve -var="access_key=${AWS_ACCESS_KEY}" -var="secret_key=${AWS_SECRET_KEY}"'
      }
    }
  }
}
