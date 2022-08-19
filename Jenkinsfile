pipeline{
	agent any
    parameters{
    string(name : 'VERSION',defaultValue : '', description : '')
    choice(name : 'ENV', choices : ['DEV','STG','PROD'], description : '')
    booleanParam(name : 'SKIP-TESTS', defaultValue : false, description : '')
    }
	stages{
    		stage("clean"){
    			steps{
    				echo "cleaning project..."
    			}
    		}
    		stage("build"){
    			steps{
    				echo "building project..."
    			}
    		}
    		stage("tests"){
    		    when{
    		        expression{
    		         params.SKIP-TESTS == false
    		        }
    		    }
                			steps{
                				echo "running tests..."
                			}
            }
    		stage("deploy"){
    			steps{
    				echo "deploying project with version - ${params.VERSION}..."
    			}
    		}
    	}

}