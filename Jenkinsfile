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
	post {
        failure {
              mail to: 'saisura3342@gmail.com',
                subject: "FAILED: Build ${env.JOB_NAME}", 
                body: "Build failed ${env.JOB_NAME} build no: ${env.BUILD_NUMBER}.\n\nView the log at:\n ${env.BUILD_URL}\n\nBlue Ocean:\n${env.RUN_DISPLAY_URL}"
        }
    
    success{
            mail to: 'saisura3342@gmail.com',
                subject: "SUCCESSFUL: Build ${env.JOB_NAME}", 
                body: "Build Successful ${env.JOB_NAME} build no: ${env.BUILD_NUMBER}\n\nView the log at:\n ${env.BUILD_URL}\n\nBlue Ocean:\n${env.RUN_DISPLAY_URL}"
        }
        
        aborted{
            mail to: 'saisura3342@gmail.com',
                subject: "ABORTED: Build ${env.JOB_NAME}", 
                body: "Build was aborted ${env.JOB_NAME} build no: ${env.BUILD_NUMBER}\n\nView the log at:\n ${env.BUILD_URL}\n\nBlue Ocean:\n${env.RUN_DISPLAY_URL}"
        }
    }
}
