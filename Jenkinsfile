pipeline {
  environment {
    registry = "sekhar111/dockertest"
    registryCredential = "docker-hub-credentials"
	dockerImage = ''
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
         dockerImage = docker.build(registry) + ":$BUILD_NUMBER"
        }
	}
    stage('Deploy Image') {
      steps{
          docker.withRegistry( 'https://hub.docker.com/', registryCredential ) {
          dockerImage.push()
      		}
	  }
  }
}
}
