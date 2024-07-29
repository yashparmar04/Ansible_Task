pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/yashparmar04/Ansible_Task.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("yashparmar04/ansible_task")
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    dockerImage.inside {
                        sh 'npm test'
                    }
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'Arrow@158165') {
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }
}
