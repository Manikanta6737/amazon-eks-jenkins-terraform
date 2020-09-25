pipeline {
    agent any
     stages {
        stage('Build & Push docker image to ECR') {
            steps {
                sh 'docker build -t test .'
                sh 'docker tag test:latest 070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository:latest'
		withDockerRegistry([url: "https://070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository",credentialsId: "ecr:us-east-1:awskey"])
		sh 'docker push 070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository:latest'
         }
      }
   }   
}
