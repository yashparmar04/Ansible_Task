pipeline {
    agent any
 
    stages {
 
	stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git url :'https://github.com/yashparmar04/Ansible_Task ', branch: 'develop'

            }
        }
 
        stage('Build Docker Image') {
            steps {
                script {
		    sh "cat Dockerfile"
                    sh "sudo docker build -t yashparmar04/my_repo_ansible ."
		    sh "sudo docker login --username yashparmar04 --password Arrow@158165"
		    sh "sudo docker push yashparmar04/my_repo_ansible:latest"
                }
            }
        }
 
	stage('Run Tests'){
	    steps {
		script {
		    echo 'Test Running ...'
		}
            }
	}
    }
 
    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
has context menu
