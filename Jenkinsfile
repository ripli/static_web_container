pipeline {
    agent any
    stages {
	stage('Clone repository') {
		checkout scm
	}
    	stage('Build docker image') {
    	    steps {
    		    app = docker.build("static_web_container")
    	    }
    	}
    	stage('Deploy') {
    	    steps {
    		    sh 'echo "deploy-test"'
    	    }
    	}
    }
}

