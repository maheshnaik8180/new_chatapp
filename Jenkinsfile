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
    }
}
