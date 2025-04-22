pipeline {
    agent {
        label 'Build-agent-2'
    } 

    stages {
        stage('Deploy to AKS') {
            steps {
                withCredentials([file(credentialsId: 'aks-kubeconfig', variable: 'KUBECONFIG')]) {
                    sh '''
                        echo "Using kubeconfig from Jenkins credential..."
                        kubectl get nodes
                        helmfile sync
                    '''
                }
            }
        }
    }
}
