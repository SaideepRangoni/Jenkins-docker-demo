pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/SaideepRangoni/Jenkins-docker-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodeapp:v1 .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop nodeapp || true
                docker rm nodeapp || true

                docker run -d \
                --name nodeapp \
                -p 3000:3000 \
                nodeapp:v1
                '''
            }
        }
    }
}
