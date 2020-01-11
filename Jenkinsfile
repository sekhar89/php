pipeline {
        agent any
        environment {
                registry = "demo"
                registry1 = "https://929747456480.dkr.ecr.us-east-1.amazonaws.com"
                registryCredential = "my-aws-keys"
        }

        stages {
            stage("Build") {
                steps {
                    script {
                        docker.withTool("docker") {
                                dockerImage = docker.build registry
                        }
                     }
                }
            }

            stage("Push") {
                steps {
                    script {
                        docker.withTool("docker") {

                            docker.withRegistry('https://929747456480.dkr.ecr.us-east-1.amazonaws.com','ecr:us-east-1:my-aws-keys') {
                                docker.image('demo').push('latest')
                            }
                        }
                    }
                }
           }
		   stage("Docker push") {
			   steps {
				   script {
					   docker.withRegistry('https://hub.docker.com','docker-hub-credentials') {
						   docker.image('demo').push('latest')
					   }
				   }
			   }
		   }
        }
}
