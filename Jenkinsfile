pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git credentialsId: 'github-creds',
                url: 'https://github.com/kkanishk26/devsecops-game.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t tetris-game:v1 ./app'
            }
        }

        stage('Security Scan - Trivy') {
            steps {
                sh 'trivy image tetris-game:v1'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f tetris-container || true
                docker run -d -p 8090:80 --name tetris-container tetris-game:v1
                '''
            }
        }
    }
}
