pipeline {
    agent any
     stages {
        stage('Build & Push docker image to ECR') {
            steps {
                sh 'docker build -t test-repository .'
                sh 'docker tag test-repository:latest 070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository'
		withDockerRegistry([url: "https://070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository",credentialsId: "ecr:us-east-1:demo-ecr-credentials"])
		sh 'docker push <URI>'
         }
      }
   }   
}
