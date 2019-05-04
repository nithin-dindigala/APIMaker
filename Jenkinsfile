pipeline{
    agent any
    tools {
      maven 'maven'
      nodejs 'node'
      git 'Default'
    }

    environment{
        
        def gitPath = "C:\\Users\\anu\\Desktop\\Cognizant\\Jenkins\\APIMAKER\\APIMakrRepo\\APIMaker"
        def apimkrPath = "C:\\Users\\anu\\Desktop\\Cognizant\\APIMaker\\ctsapimakr_v3\\ctsapimakr"
    }
    stages{
        stage('Git Connection'){
            
            steps{
                
                dir(gitPath){
                   script{
                    def files = sh(returnStdout:true, script:'git diff --name-only')
                    echo "${files}"
                   }
                   
                }
            }
            
        }
        
        stage('APIMaker-CreateAPI'){
            
            steps{
                
                dir(apimkrPath){
                   /* bat('ctsapimakr initialize customer-2 nithindindigala-eval swagger.yaml')*/
                }
            }
            
        }
        stage('APIMaker-TestAPI'){
            
            steps{
                
                echo "test"
            }
            
        }
        stage('APIMaker-DeployAPI'){
            
            steps{
                
                echo "test"
            }
            
        }
    }
}