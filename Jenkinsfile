pipeline {
    agent any
     stages {
	stage('login_ecr') {
    	    steps {
       		script {
		 withDockerRegistry(credentialsId: 'ecr:us-east-1:awskey', url: 'https://console.aws.amazon.com/ecr/repositories/test-repository/?region=us-east-1')        }    
    }
}
        stage('Build & Push docker image to ECR') {
            steps {
                sh 'docker build -t test .'
		sh 'docker tag test:latest 070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository:latest'
		sh 'docker push 070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository:latest'
         }
      }
   }   
}
