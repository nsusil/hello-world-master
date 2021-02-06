pipeline{
    
    agent any
    
    environment {
    PATH= "/usr/share/maven;$PATH"
    }
    
    stages{
        
        stage("Git Checkout"){
            steps{
               git 'https://github.com/nsusil/hello-world-master.git'
            }
        }
        stage("Maven Build"){
            steps{
               sh 'mvn clean install package'
            }
        }
        
        stage("deploy tomcat"){
            steps{
               
               sshagent(['tomcat-user']) {
                   
                   sh """
                        scp -o StrictHostKeyChecking=no webapp/target/*.war ubuntu@54.153.65.176:/opt/tomcat9/webapps
                        ssh ubuntu@54.153.65.176 /opt/tomcat/bin/shutdown.sh
                        ssh ubuntu@54.153.65.176 /opt/tomcat/bin/startup.sh
                
                   """
               }
         
                
            }
        }
        
        
        
        }
    
    }
    
    
    
