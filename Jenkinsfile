pipeline {
    agent any
    stages {
		stage('SCM Checkout'){
		 git 'https://github.com/ravibs1994/new_chatapp'
		 }
     stage('build') {
       steps {
         rsync -avh -e 'ssh -i /var/lib/jenkins/keypairForChatApp.pem' /var/lib/jenkins/workspace/JenkinsChatapp/ ubuntu@10.0.1.66:/home/ubuntu/new_chatapp/

				 ssh -i /var/lib/jenkins/keypairForChatApp.pem ubuntu@10.0.1.66 sudo systemctl stop django.service
				 ssh -i /var/lib/jenkins/keypairForChatApp.pem ubuntu@10.0.1.66 sudo systemctl start django.service

            }
        }
    }
}
