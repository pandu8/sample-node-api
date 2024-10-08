pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Build Docker image
                    sh 'docker build -t node-api-img .'
                }
            }
        }
        stage('Push to ECR') {
            steps {
                script {
                    // Login to ECR
                    sh 'aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 725996091944.dkr.ecr.ap-south-1.amazonaws.com'
                    // Tag and push the image
                    sh 'docker tag node-api-img:latest 725996091944.dkr.ecr.ap-south-1.amazonaws.com/node-ecr:latest'
                    sh 'docker push 725996091944.dkr.ecr.ap-south-1.amazonaws.com/node-ecr:latest'
                }
            }
        }
    }
}
