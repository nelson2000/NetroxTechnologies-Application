
    
    pipeline{ 
    
    agent any 
    
    tools {
            maven 'maven38'
        }
    stages{ 

            stage('Initilization'){

		            steps{
                    sh 'echo This is the NetroxApp Project Dev Environment'

		                }
	                } 
	        stage('CodeCheckout'){
		    
		            steps{
                        sh 'echo This is the code checkout stage'
        
      
                    }
	            } 

	        stage('CodeBuild'){

		            steps{
                        sh 'echo This is the Code build stage'
                        sh 'mvn package'
		            }
	            } 

            stage('CodeTesting'){

		            steps{
                            sh 'echo This is the Code Testing'
                        }
                    } 

	        stage('CodeQuality'){

		            steps{
                            sh 'echo This is the Code Quality stage'
                                         
		                }

	                } 

	        stage('BackupArtifact'){

		            steps{
                            sh 'echo This is the artifact backup stage'
                      

		                }

	                } 

            stage('ApprovalToDeploy'){

		            steps{
                            sh "echo Approval required"
                            timeout(time:2, unit:'DAYS'){
                            input message:'Approval for Production'
		                    }
                        }
                    } 

	        stage('DeployToProdServer1'){

		            steps{
		                    sh 'echo This is the deployment stage'
                           
		                }

	                } 
	
	        stage('DeployToProdServer2'){
	    
	                steps{
	                        sh 'echo This is another artifact storage'

	                    }
                	}

            stage('DeployToProdServer2'){
	    
	                steps{
	                        sh 'echo This is another artifact storage'

	                    }
                	}

        
    }

}
