pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-demo-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f demo || true
                docker run -d -p 3000:3000 --name demo jenkins-demo-app
                '''
            }
        }
    }
}
