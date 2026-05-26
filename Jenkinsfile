pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-siddu1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://DBD89E21E5AD9D8B9C7F5C71064E4F97.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-siddu1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://DBD89E21E5AD9D8B9C7F5C71064E4F97.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
