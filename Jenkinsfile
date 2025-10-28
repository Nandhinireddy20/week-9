pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t registration:v1 .'
            }
        }
        stage('Automated UI Test') { 
            steps { 
                 bat 'python C:/DevOps/week-2/test_registration.py' 
            } 
        } 
        stage('Push to Docker Hub') {
            steps {
                bat 'docker tag registration:v1 nandhinireddy20/registration:v1'
                bat 'docker push nandhinireddy20/registration:v1'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f C:/Devops/Week-2/deployment.yaml'
                bat 'kubectl apply -f C:/Devops/Week-2/service.yaml'
            }
        }
        stage('Automated UI Test') {
            steps {
                bat 'python C:\Devops\Week-2\test_registration.py'
            }
        }
    }
}
