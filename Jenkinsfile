pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
	PROJECT = 'test-repository'
	IMAGE = "$PROJECT"
	ECRURL = "https://070999721344.dkr.ecr.us-east-1.amazonaws.com/test-repository"
	ECRCRED = "ecr:us-east-1:awskey"
    }
     stages {
	  stage('Image Build'){
	    steps {
		script{
		       docker.build('$IMAGE')
		    }
	       }
	  }
	     stage('Push image'){
	    steps {
		script 
		    {
		       docker.withRegistry(ECRURL, ECRCRED)
			  {
			     docker.image(IMAGE).push()
			  }
		    }
	    }
	 }
     }
}
