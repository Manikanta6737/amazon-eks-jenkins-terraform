pipeline {
    agent any
     stages {
    	  stage('Build & Push docker image to ECR') {
            steps {
                sh 'docker build -t test .'
		sh 'docker tag test:latest 070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository:latest'
		withEnv(['AWS_ACCESS_KEY_ID     = credentials(\'jenkins-aws-secret-key-id\')', 'AWS_SECRET_ACCESS_KEY = credentials(\'jenkins-aws-secret-access-key\')']) 
		sh 'docker push 070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository:latest'
         }
      }
   }   
}
