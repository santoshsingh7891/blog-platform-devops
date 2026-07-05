pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/santoshsingh7891/blog-platform-devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t blog-platform .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f blog-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name blog-container -p 8081:80 blog-platform'
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful!'
        }

        failure {
            echo 'Deployment Failed!'
        }
    }
}
