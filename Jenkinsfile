@Library('my-shared-librabry') _

pipeline {
    agent any

    parameters{
        string(name: 'ImageName', description: "Name of docker build", defaultValue:  'javapp')
        string(name: 'ImageTag', description: "Tag of docker build", defaultValue:  'v1')
        string(name: 'hubUser', description: "Name of docker build", defaultValue:  'imsuyog')
    }
	
    options {
		skipDefaultCheckout(true)
   }

    stages{
        
        stage('Git Checkout'){ 
        steps {
            script{
				git branch: "main", url: 'https://github.com/suyogIsdevopsEngineer/Java_app.git'
			}             
            }
        }

        stage('Unit test Maven'){
        steps {
			script{
				mvnTest()
			}  
        }
        }
        
        stage('Integration Test maven'){
            steps{
				script{
					mvnIntegration()
				}
            }
        }

            
            stage('Static code Analysis: Sonarqube'){
            steps{
				script{
                    
					def SonaraqubeCredentialsId = 'sonar'
                    sonarStaticAnalysis(SonaraqubeCredentialsId)
				}
            }
        }

        stage('Maven Build : maven'){
            steps{
				script{
                    
                    mvnBuild()
				}
            }
        }

        stage('docker Build : maven'){
            steps{
				script{
                    
                    dockerBuild("${params.ImageName}","${params.hubUser}","${params.ImageTag}")
				}
            }
        }
    }
    }