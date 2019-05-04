pipeline{
    agent any
    tools {
      maven 'maven'
      nodejs 'node'
      git 'Default'
    }
def files = ''
def gitPath = "C:\\Users\\anu\\Desktop\\Cognizant\\Jenkins\\APIMAKER\\APIMakrTargetRepo\\APIMaker\\"
def apimkrPath = "C:\\Users\\anu\\Desktop\\Cognizant\\APIMaker\\ctsapimakr_v3\\ctsapimakr\\"
def org = "nithindindigala-eval"
    environment{
        
        NODE_PATH = "C:\\Users\\anu\\AppData\\Roaming\\npm\\node_modules"
    }
     
    stages{
   
   
    
        stage('Git Connection'){
            
            steps{
                
                dir(gitPath){
                   script{
                    sh('git pull')
                    files = sh(returnStdout:true, script:'git show --pretty="" --name-only')
                    echo "${files}"
                   
                   }
                   
                }
            }
            
        }
        
        stage('APIMaker-CreateProxy'){
            
            steps{
                script{
                
                def oasPath = apimkrPath+files;
                echo "${oasPath}"
                def batscpt = files+' '+org+' '+oasPath
                dir(apimkrPath){
                   bat("ctsapimakr initialize ${batscpt}")
                }
                           
            }
            }
            
        }
        stage('APIMaker-TestProxy'){
            
            steps{
                
                echo "test"
            }
            
        }
        stage('APIMaker-DeployProxy'){
            
            steps{
                
                echo "test"
            }
            
        }
    }
}