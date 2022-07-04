pipeline{
	agent any
	parameters{
		choice(name: 'VERSION', choices: ['1.0.0', ['1.0.1']], description: '')
		booleanParam(name: 'executeTests', defaultValue: true, description: '')
	}
	stages{
	  stage("build"){
		steps{
		  echo 'building the application'
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
		}
	  }
	  stage("deploy"){
		steps{
		  echo 'deploying the application'
		  echo "deploying version ${VERSION}"
		}
	  }
	}  
}
