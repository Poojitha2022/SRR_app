pipeline{
    agent any
    
    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }
    stages{
        stage("Git Checkout"){
            steps{
                git 'https://github.com/Poojitha2022/SRR_app'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
        }
        stage("deploy-dev"){
            steps{
			    deploy adapters: [tomcat9(credentialsId: 'tomcat-vm', path: '', url: 'http://34.172.246.148:8080/')], contextPath: 'webapps', onFailure: false, war: 'target/*.war'  
                
            }
            
            }
        }
    }
