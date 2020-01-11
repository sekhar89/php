pipeline {
  environment {
    registry = "sekhar111/dockertest"
    registryCredential = "docker-hub-credentials"
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git "https://github.com/sekhar89/php.git"
      }
    }
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
  }
}
