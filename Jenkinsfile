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
                sh 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t java-app:v1 .'
            }
        }

        stage('Deploy Kubernetes') {
            steps {
                sh 'minikube image load java-app:v1'
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
}