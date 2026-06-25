pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/USERNAME/REPOSITORY.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop myapp || true
                docker rm myapp || true
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d --name myapp -p 8081:80 myapp'
            }
        }

    }
}
