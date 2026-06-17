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
<<<<<<< HEAD
          powershell '''
          $password = aws ecr get-login-password --region us-east-2
          docker login --username AWS --password $password 238641751057.dkr.ecr.us-east-2.amazonaws.com
=======
          sh '''
          aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 238641751057.dkr.ecr.us-east-2.amazonaws.com
>>>>>>> ff86478b1f9aa6509e90b7c57c4edfb9ba27e0a3
          '''
        }
      }
    }
    stage('Build docker image') {
      steps {
<<<<<<< HEAD
        powershell '''
=======
        sh '''
>>>>>>> ff86478b1f9aa6509e90b7c57c4edfb9ba27e0a3
        docker build -t test:django .
        docker tag test:django 238641751057.dkr.ecr.us-east-2.amazonaws.com/test:django
        '''
      }
    }
    stage('Pushing image to ECR') {
      steps {
<<<<<<< HEAD
        powershell '''
=======
        sh '''
>>>>>>> ff86478b1f9aa6509e90b7c57c4edfb9ba27e0a3
        docker push 238641751057.dkr.ecr.us-east-2.amazonaws.com/test:django
        '''
      }
    }
  }
}