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
    	    app = docker.build("prili/static_web")
	}
    	}
	stage('Push Docker Image') {
	steps {
		docker.withRegistry('https://registry.hub.docker.com', '')
	}
	}
    	stage('Deploy') {
	steps {
    	    sh 'echo "deploy-test"'
	}
    	}
    }
}

