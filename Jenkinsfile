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
		sh 'echo "Hello visitor! ${BUILD_NUMBER}" > index.html'
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
				app.push("latest")
			}
                }
	  }
	}
	stage('Deploy To k8s') {
	  steps {
	    sh 'curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.15.0/bin/linux/amd64/kubectl'
	    sh 'chmod +x ./kubectl'
	    sh 'mv ./kubectl /usr/local/bin/kubectl'
	    sh 'mv config ~/.kube/config'
	    sh '/usr/local/bin/kubectl replace -f static_web_deployment.yaml'
	  }
	}
  }
}

