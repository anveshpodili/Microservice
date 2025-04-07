 pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'EKS-1', 
                    contextName: '', 
                    credentialsId: 'k8s-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://BB8493EB4E9CA638B0D735D1F1F261FA.gr7.ap-south-1.eks.amazonaws.com'
                ]]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        stage('Verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'EKS-1', 
                    contextName: '', 
                    credentialsId: 'k8s-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://BB8493EB4E9CA638B0D735D1F1F261FA.gr7.ap-south-1.eks.amazonaws.com'
                ]]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
