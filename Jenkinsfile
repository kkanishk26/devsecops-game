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
                sh '''
                if ! command -v trivy &> /dev/null
                then
                    echo "Installing Trivy..."
                    sudo apt-get update
                    sudo apt-get install -y wget apt-transport-https gnupg lsb-release
                    wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
                    echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee /etc/apt/sources.list.d/trivy.list
                    sudo apt-get update
                    sudo apt-get install -y trivy
                fi

                trivy image $IMAGE_NAME:$IMAGE_TAG
                '''
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
