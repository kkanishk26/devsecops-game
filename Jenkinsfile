pipeline {
    agent any

    environment {
        IMAGE_NAME = "tetris-game"
    }

    stages {

        stage('Clone Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:v1 ./app'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f tetris-container || true
                docker run -d -p 8090:80 --name tetris-container $IMAGE_NAME:v1
                '''
            }
        }
    }
}
