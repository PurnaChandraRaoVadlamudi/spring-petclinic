pipeline {
  agent any

  environment {
    MAVEN_OPTS = "-Dmaven.test.failure.ignore=false"
  }

  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/YOUR_USERNAME/spring-petclinic.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean compile'
      }
    }

    stage('Unit Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Approval') {
      steps {
        input message: 'Do you want to deploy to Dev?', ok: 'Yes, Deploy'
      }
    }

    stage('Deploy to Dev') {
      steps {
        echo 'Deploying to Dev Environment...'
        // Replace with your deploy script
        sh 'echo Deploy script goes here'
      }
    }
  }

  post {
    success {
      echo 'Pipeline completed successfully.'
    }
    failure {
      echo 'Pipeline failed.'
    }
  }
}
