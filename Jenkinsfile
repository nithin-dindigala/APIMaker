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
                    files = sh(returnStdout:true, script:'git show --pretty="" --name-only').trim()
                    echo "${files}"
                    def filelist = []
                   filelist = files.tokenize('/')
                    def fileName = filelist[0] 
                    def fileNmExt = filelist[1]
                    echo "${fileName}"
                    echo "${fileNmExt}"
                   }
                   
                }
            }
            
        }
        
        stage('APIMaker-CreateProxy'){
            
            steps{
                script{
                
                def oasPath = apimkrPath+fileNmExt;
                def gitpullpath = gitPath+fileNmExt;
                bat("COPY ${gitpullpath} ${oasPath}")
                dir(apimkrPath){
                   bat("ctsapimakr initialize ${fileName} ${org} ${fileNmExt}")
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