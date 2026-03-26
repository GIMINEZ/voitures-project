pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/GIMINEZ/voitures-project.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                dir('voitures-backend') {       // ← se positionner dans le sous-dossier
                    sh './mvnw clean install'
                }
            }
        }
        stage('Test') {
            steps {
                dir('voitures-backend') {
                    sh './mvnw test'
                }
            }
        }
        stage('Package') {
            steps {
                dir('voitures-backend') {
                    sh './mvnw package'
                }
            }
        }
    }
    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}