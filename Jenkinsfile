pipeline {
    agent any

    stages {
        stage('Deploy To kubernertes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '11microservice', contextName: '', credentialsId: 'k8-token', namespace: '11microserviceapp', serverUrl: 'https://21125BA4CA5B7B91000467EAFB3603A4.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '11microservice', contextName: '', credentialsId: 'k8-token', namespace: '11microserviceapp', serverUrl: 'https://21125BA4CA5B7B91000467EAFB3603A4.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n 11microserviceapp"
                }
            }
        }
    }
}
