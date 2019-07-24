pipeline {
    agent any

    stages {
	stage('Clone repository') {
		checkout scm
	}
    	stage('Build docker image') {
    	    app = docker.build("prili/static_web")
    	}
	stage('Push Docker Image') {
		docker.withRegistry('https://registry.hub.docker.com', '')
	}
    	stage('Deploy') {
    	    sh 'echo "deploy-test"'
    	}
    }
}

