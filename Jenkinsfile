pipeline {
    agent any
     stages {
    	  stage('Build & Push docker image to ECR') {
            steps {
                sh 'docker build -t test .'
		sh 'docker tag test:latest 070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository:latest'
		withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'awskey', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
		sh 'docker push 070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository:latest'
         }
      }
   }   
}
