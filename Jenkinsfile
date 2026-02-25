pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/kkanishk26/devsecops-game.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t tetris-game:v1 ./app'
            }
        }

        stage('Run Security Scan') {
            steps {
                dependencyCheck additionalArguments: '--scan ./app', odcInstallation: 'Default'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop tetris-game || true
                docker rm tetris-game || true
                docker run -d -p 8090:80 --name tetris-game tetris-game:v1
                '''
            }
        }
    }
}
