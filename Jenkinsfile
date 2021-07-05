pipeline{
    agent any

    environment{
        DOCKERHUB_CREDENTIALS = credentials('kbogdanski')
    }
    node{
    stages {
        stage('Build'){
            steps{
                sh 'docker build -t worker:2.0 ./worker ' 
            }
        }
        stage('Login') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push'){
            steps {
                sh 'docker push worker:2.0'
            }
        }
    }
    
    post {
        always {
            sh 'docker logout'
        }
    }
    }

}