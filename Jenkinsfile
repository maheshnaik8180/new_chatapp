pipeline {
    agent any
    stages {
	stage('SCM Checkout'){
	    steps{
	        git 'https://github.com/ravibs1994/new_chatapp'
	    }
        }
        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t jenkinsbackend /var/lib/jenkins/workspace/DockerJenkinsPipeline'
                sh 'sudo docker tag jenkinsbackend:latest 646702086747.dkr.ecr.ap-south-1.amazonaws.com/jenkinsbackend'
                sh 'sudo docker push 646702086747.dkr.ecr.ap-south-1.amazonaws.com/jenkinsbackend:latest'
            }
        }
        stage('Pull Docker Image') {
            steps{
	            sh 'ssh -i /var/lib/jenkins/keypairForChatApp.pem -o StrictHostKeyChecking=no ubuntu@10.0.2.129 sudo docker pull 646702086747.dkr.ecr.ap-south-1.amazonaws.com/jenkinsbackend:latest'
            }
        }
        stage('Run Docker Image') {
            steps{
	            sh 'ssh -i /var/lib/jenkins/keypairForChatApp.pem -o StrictHostKeyChecking=no ubuntu@10.0.2.18 sudo kubectl delete pods backend-74554b5fd9-sd9bp' 
            }
        }
    }
}
