pipeline {
    agent {
        label 'Build-agent-2'
    } 
     environment {
        KUBECONFIG = credentials('aks-kubeconfig')  
    }

    stages {
        stage('Deploy to AKS') {
            steps {
                withCredentials([file(credentialsId: 'aks-kubeconfig', variable: 'KUBECONFIG')]) {
                    sh '''
                        echo "Using kubeconfig from Jenkins credential..."
                        kubectl get nodes
                        echo "Deploying to AKS using Helmfile..."
                        helmfile sync
                    
                    '''
                }
            }
        }
    }
}
