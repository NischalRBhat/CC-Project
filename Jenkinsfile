pipeline {
    agent any
    stages {
        stage('Build Docker Images') {
            steps {
                script {
                    bat 'docker build -t serv1 ./auth-service'
                    bat 'docker build -t serv2 ./product-service'
                    bat 'docker build -t serv3 ./order-service'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    bat 'kubectl delete deployments --all'
                    bat 'kubectl delete services --all'
                    bat 'kubectl apply -f ./k8s/'
                }
            }
        }
    }
}
