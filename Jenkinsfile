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
               
                sshagent(['tomcat-new']) {
                    
                    sh """
                        scp -o StrictHostKeyChecking=no webapp/target/*.war ubuntu@172.31.14.14:/opt/tomcat8/webapps
                        ssh ubuntu@172.31.14.14 /opt/tomcat8/bin/shutdown.sh
                        ssh ubuntu@172.31.14.14 /opt/tomcat8/bin/startup.sh
                    
                    """
                }
                
            }
        }
        
        
        
        }
    
    }
    
    
    
