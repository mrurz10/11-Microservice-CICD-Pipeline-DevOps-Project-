pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
          withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'eks', namespace: 'webapps', serverUrl: 'https://3A67878AB79AF07FBB6737BE13DE289E.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml -n argocd"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'eks', namespace: 'webapps', serverUrl: 'https://3A67878AB79AF07FBB6737BE13DE289E.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps -n argocd"
                }
            }
        }
    }
}
