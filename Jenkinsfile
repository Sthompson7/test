pipeline {
  agent any
  environment {
    VENV = 'venv'
  }
  stages {
    stage('Checkout Out') {
      steps {
        git branch: 'main', url: 'https://github.com/Sthompson7/test.git'
      }
    }
    stage('Login to ECR') {
      steps {
        withAWS(region: 'us-east-2', credentials: 'aws-creds') {
          sh '''
          aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 238641751057.dkr.ecr.us-east-2.amazonaws.com
          '''
        }
      }
    }
    stage('Build docker image') {
      steps {
        sh '''
        docker build -t test:django .
        docker tag test:django 238641751057.dkr.ecr.us-east-2.amazonaws.com/test:django
        '''
      }
    }
    stage('Pushing image to ECR') {
      steps {
        sh '''
        docker push 238641751057.dkr.ecr.us-east-2.amazonaws.com/test:django
        '''
      }
    }
  }
}
