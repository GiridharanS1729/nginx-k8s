pipeline {
    agent any
    environment {
        KUBECONFIG = credentials('kubeconfig-id')  // Load kubeconfig from Jenkins credentials
    }
    stages {
        stage('Checkout Code') {
            steps {
                git credentialsId: 'github_seccred', url: 'https://github.com/GiridharanS1729/nginx-k8s.git'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f nginx-deployment.yml'  // Deploy to Kubernetes
            }
        }
        stage('Verify Deployment') {
            steps {
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }
    }
}
