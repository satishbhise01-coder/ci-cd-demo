pipeline {
    agent any

    environment {
        IMAGE_NAME = "ci-cd-demo"
        CONTAINER_NAME = "ci-cd-container"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/YOUR_USERNAME/ci-cd-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }
}