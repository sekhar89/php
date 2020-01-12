node {
	
  checkout scm
  def dockerImage

  stage('Build image') {
    dockerImage = docker.build("sekhar111/dockertest:test")
  }

  stage('Push image') {
    docker.withRegistry('https://hub.docker.com/repository/docker/', 'docker-hub-credentials) {
      docker.push(dockerImage)
    }
  }

}
