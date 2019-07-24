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
		sh 'echo "${env.BUILD_NUMBER}" > index.html'
	        script {
	          app = docker.build("prili/static_web")
	        }
          }
        }
	stage('Push Docker Image') {
	  steps {
		script {
			docker.withRegistry( '', 'f192a746-f214-4aef-adc1-978b20c5b188') {
				app.push("${env.BUILD_NUMBER}")
			}
                }
	  }
	}
  }
}

