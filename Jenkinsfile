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
                  sh 'docker build -t jenkinsbackend /var/lib/jenkins/workspace/DockerJenkinsPipeline'
                  sh 'docker tag jenkinsbackend:latest 646702086747.dkr.ecr.ap-south-1.amazonaws.com/jenkinsbackend'
                  sh 'docker push 646702086747.dkr.ecr.ap-south-1.amazonaws.com/jenkinsbackend:latest'
         }
       }
    }
}
