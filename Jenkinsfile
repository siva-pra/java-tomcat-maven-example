pipeline{
    agent{
        label "maven"
    }
    tools{
        maven 'MVN_HOME'
    }
    triggers { 
        pollSCM('H * * * 1-5')
    }
    stages{
        stage("SCM"){
            steps{
               git 'https://github.com/siva-pra/java-tomcat-maven-example.git'
            }
        }
        stage("BUILD"){
            steps{
                 sh '''mvn clean package
'''
            }
           
        }
        stage("deploy to tomcat"){
            steps{
                sshagent(['maven-node']) {
                     sh 'scp -o StrictHostKeyChecking=no project2/target/java-tomcat-maven-example.war ubuntu@34.211.148.129:8080:/opt/tomcat/webapps/manager/'
    
               }
            }
        }
    }
   
}
