
    
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
			checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-cred', url: 'https://github.com/nelson2000/NetroxTechnologies-Application.git']]])
        
      
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
                             //sh 'mvn sonar:sonar'            
		                }

	                } 

	        stage('BackupArtifact'){

		            steps{
                            sh 'echo This is the artifact backup stage'
                      	    //sh 'mvn deploy'

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
				    deploy adapters: [tomcat9(credentialsId: 'tomcat1', path: '', url: 'http://192.168.56.17:8080/')], contextPath: null, war: '**/target/*.war'
				    
	                } 

			}
	
	        stage('DeployToProdServer2'){
	    
	                steps{
	                        sh 'echo This is another artifact storage'
				
				deploy adapters: [tomcat9(credentialsId: 'tomcat1', path: '', url: 'http://192.168.56.17:8080/')], contextPath: null, war: '**/target/*.war'

	                    }
                	}

            	stage('DeployToProdServer3'){
	    
	                steps{
	                        sh 'echo This is another artifact storage'
				
				deploy adapters: [tomcat9(credentialsId: 'tomcat1', path: '', url: ' http://192.168.56.12:8080/')], contextPath: null, war: '**/target/*.war'

	                    }
                	}

        
    	}

	}
