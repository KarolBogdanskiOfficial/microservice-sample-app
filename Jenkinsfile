pipeline {
	
	agent any
	
    	environment {
		GITHUB_CREDENTIALS = credentials('github-KBO')
    	}
    	stages {
            stage('build') {
                steps {
		    sh 'docker build -t ghcr.io/karolbogdanskiofficial/microservice-sample-app/worker:latest ./worker'
                }
            }

	    stage('push') {
                steps { 
	            sh 'docker push ghcr.io/karolbogdanskiofficial/microservice-sample-app/worker:latest'
		}
	    }
    	}
	post {
	    failure {  
                mail bcc: '', body: "<b>ERROR</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Build number -> ${env.BUILD_NUMBER}", to: "kbogdanski@griddynamics.com";  
            } 
	}
}