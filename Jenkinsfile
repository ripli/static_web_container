pipeline {
    agent any

    stages {
	stage('Clone repository') {
	  steps {
		checkout scm
	  }
	}
        stage('Build docker image') {
	  steps {
	        script {
	          dockerImage = docker.build "prili/static_web" + ":$BUILD_NUMBER"
	        }
          }
        }
	stage('Push Docker Image') {
	  steps {
		script {
			docker.withRegistry('', 'docker-login')
			dockerImage.push()
                }
	  }
	}
  }
}

