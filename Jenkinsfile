pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/sridhar2822/react-devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t react-devops-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop react-container || true'
                sh 'docker rm react-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name react-container react-devops-app'
            }
        }

    }
}