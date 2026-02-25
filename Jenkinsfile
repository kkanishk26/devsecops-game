pipeline {
    agent any

    environment {
        IMAGE_NAME = "tetris-game"
        IMAGE_TAG = "v1"
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/kkanishk26/devsecops-game.git',
                credentialsId: 'github-creds'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG ./app'
            }
        }

        stage('Security Scan - Trivy') {
            steps {
                sh 'trivy image $IMAGE_NAME:$IMAGE_TAG'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f tetris-container || true
                docker run -d -p 8090:80 --name tetris-container $IMAGE_NAME:$IMAGE_TAG
                '''
            }
        }
    }
}
