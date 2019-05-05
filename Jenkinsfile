def files = ''
def gitPath = 'C:\\Users\\anu\\Desktop\\Cognizant\\Jenkins\\APIMAKER\\APIMakrTargetRepo\\APIMaker\\'
def apimkrPath = 'C:\\Users\\anu\\Desktop\\Cognizant\\APIMaker\\ctsapimakr_v3\\ctsapimakr\\'
def org = 'nithindindigala-eval'
pipeline{
    agent any
    tools {
      maven 'maven'
      nodejs 'node'
      git 'Default'
    }

    environment{
        
        NODE_PATH = "C:\\Users\\anu\\AppData\\Roaming\\npm\\node_modules"
        
    }
     
    stages{
   
      
        stage('Git Pull'){
            
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
                def gitpullpath = gitPath+files;
                def cpycmd = gitpullpath+' '+oasPath;
                def apimkrcmd = files+' '+org+' '+oasPath;
                echo "${cpycmd}"
                bat "COPY ${gitpullpath} ${oasPath}"
                dir(apimkrPath){
                   bat("ctsapimakr initialize ${apimkrcmd}")
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