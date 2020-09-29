pipeline {
    agent any
    environment {
        VERSION = "$BUILD_NUMBER"
	PROJECT = 'test-repository'
	IMAGE = "$PROJECT:$VERSION"
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
