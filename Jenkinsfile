pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t siddu009/adservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push siddu009/adservice:latest "
                    }
                }
            }
        }
    }
    post {

        success {
            slackSend(
                channel: '#web-app',
                color: 'good',
                message: "SUCCESS: ${env.JOB_NAME} - Build ${env.BUILD_NUMBER}"
            )
        }

        failure {
            slackSend(
                channel: '#web-app',
                color: 'danger',
                message: "FAILED: ${env.JOB_NAME} - Build ${env.BUILD_NUMBER}"
            )
        }
    }
}
