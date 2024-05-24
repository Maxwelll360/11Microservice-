pipeline {   
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'App2', contextName: '', credentialsId: 'k8-token', namespace: 'ecommerce', serverUrl: 'https://643DBFC993BB47677EE504978982EE36.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'App2', contextName: '', credentialsId: 'k8-token', namespace: 'ecommerce', serverUrl: 'https://643DBFC993BB47677EE504978982EE36.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n ecommerce"
                }
            }
        }
    }
}
