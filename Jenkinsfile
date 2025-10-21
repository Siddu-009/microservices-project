pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-siddu1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F289C2CAA8016D5BCE2E70688C451070.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-siddu1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F289C2CAA8016D5BCE2E70688C451070.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
