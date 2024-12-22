pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/NickName03/rgz', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                dir('~/avs/rgz/jenkins-app') { // Переход в директорию с приложением
                    sh 'docker build -t my-app .'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop my-app-container || true'
                sh 'docker rm my-app-container || true'
                sh 'docker run -d -p 80:80 --name my-app-container my-app'
            }
        }
    }
}
