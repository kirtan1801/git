pipeline{
	agent any
	parameters{
		choice(name: 'VERSION', choices: ['1.0.0', '1.0.1', '1.0.2'], description: '')
		booleanParam(name: 'executeTests', defaultValue: true, description: '')
	}
	stages{
	  stage("build"){
		  steps{
			  echo 'building the application'
			  archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
		  }
	  }
	  stage("test"){
		  when{
			  expression{
				  params.executeTests == true
			  }
		  }
		  steps{
			  echo 'testing the application'
			  junit '**/target/*.xml'
		  }
	  }
	  stage("deploy"){
		  when {
			  expression {
                		currentBuild.result == null || currentBuild.result == 'SUCCESS' 
			  }
		  }
		  steps{
			  echo 'deploying the application'
			  echo "deploying version ${params.VERSION}"
		  }
	  }
	}  
}
