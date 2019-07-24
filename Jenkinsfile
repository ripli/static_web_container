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
			docker.withRegistry( '', f192a746-f214-4aef-adc1-978b20c5b188')
			dockerImage.push()
                }
	  }
	}
  }
}

