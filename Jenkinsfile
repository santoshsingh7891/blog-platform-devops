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
                sh 'sudo docker build -t blog-platform .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo docker rm -f blog-platform || true
                sudo docker run -d --name blog-platform -p 8081:80 blog-platform
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
