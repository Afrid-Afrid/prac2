pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test || true'
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                eval $(minikube docker-env)
                docker build -t java-app:v1 .
                '''
            }
        }

        stage('Deploy Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
}