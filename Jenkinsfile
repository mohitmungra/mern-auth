pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/bradtraversy/mern-auth.git'
                sh 'npm install' // or whatever build commands you need
            }
        }
        stage('Test') {
            steps {
                // Add test commands here if applicable
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('your_docker_username/mern-auth:latest')
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_credentials_id') {
                        docker.image('your_docker_username/mern-auth:latest').push('latest')
                    }
                }
            }
        }
    }
}
