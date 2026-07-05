pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/santoshsingh7891/blog-platform-devops.git'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t blog-platform .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f blog-platform || true
                docker run -d --name blog-platform -p 8081:80 blog-platform
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful'
        }

        failure {
            echo 'Deployment Failed'
        }
    }
}
