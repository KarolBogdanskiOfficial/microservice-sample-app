pipeline {
	
	agent { node { label 'docker-agent' } }
	
    	environment {
		GITHUB_CREDENTIALS = credentials('github-karolbogdanski')
    	}
    	stages {
            stage('build') {
                steps {
		    sh 'docker build -t ghcr.io/karolbogdanskiofficial/microservice-sample-app/worker:latest ./worker'
                }
            }
            #stage('login') { 
	        #steps {
		    #sh 'docker login https://docker.pkg.github.com -u $GITHUB_CREDENTIALS_USR -p $GITHUB_CREDENTIALS_PSW'    
	    	#}
	    #}
	    stage('push') {
                steps { 
	            sh 'ghcr.io/karolbogdanskiofficial/microservice-sample-app/worker:latest'
		}
	    }
    	}
	post {
	    failure {  
                mail bcc: '', body: "<b>ERROR</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Build number -> ${env.BUILD_NUMBER}", to: "kbogdanski@griddynamics.com";  
            } 
	}
}