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
               
        }
    
    }
    
    
    
