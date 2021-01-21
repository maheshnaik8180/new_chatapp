pipeline {
    agent any
    stages {
	    stage('SCM Checkout'){
		    steps{
		    git 'https://github.com/ravibs1994/new_chatapp'
		 }
	    }
            stage('build') {
               steps {
                     sh 'rsync -avh -e ssh -i /var/lib/jenkins/keypairForChatApp.pem /var/lib/jenkins/workspace/JenkinsChatapp/ ubuntu@10.0.1.66:/home/ubuntu/new_chatapp/'
	             sh 'ssh -i /var/lib/jenkins/keypairForChatApp.pem ubuntu@10.0.1.66 sudo systemctl stop django.service'
	             sh 'ssh -i /var/lib/jenkins/keypairForChatApp.pem ubuntu@10.0.1.66 sudo systemctl start django.service'
         }
       }
    }
}
