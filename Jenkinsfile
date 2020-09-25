pipeline {
    agent any
     stages {
	stage('login_ecr') {
    	    steps {
       		script {
            	withDockerRegistry([url: "https://070999721344.dkr.ecr.us-east-1.amazonaws.com",credentialsId: "ecr:us-east-1:awskey"])
        }    
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
