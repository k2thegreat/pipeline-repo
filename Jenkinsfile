def gv  // declaring the variable globall to be available in all the stges
pipeline{
	agent any
    parameters{
    string(name : 'VERSION',defaultValue : '', description : '')
    choice(name : 'ENV', choices : ['DEV','STG','PROD'], description : '')
    booleanParam(name : 'SKIPTESTS', defaultValue : false, description : '') // all these params are available in the imported groovy scripts as well
    }
	stages{
			stage("init"){
				steps{
					script{
						gv = load "script.groovy"
					}
				}
			}
    		stage("clean"){
    			steps{
    				echo "cleaning project..."
    			}
    		}
    		stage("build"){
    			steps{
    				echo "building project..."
					echo 'calling buildProject from script.groovy'
					script{
						gv.buildProject()
					}
    			}
    		}
    		stage("tests"){
    		    when{
    		        expression{
    		         params.SKIPTESTS == false
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