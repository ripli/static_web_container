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
	    dockerImage = docker.build "prili/static_web" + ":$BUILD_NUMBER"
	}
    	}
	stage('Push Docker Image') {
	steps {
		docker.withRegistry('')
		dockerImage.push()
	}
	}
    	stage('Deploy') {
	steps {
    	    sh 'echo "deploy-test"'
	}
    	}
    }
}

