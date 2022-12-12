pipeline{
    agent{
        label "maven"
    }
    stages{
        stage("SCM"){
            steps{
               git 'https://github.com/ManfredWind/deploying-spring-boot-as-war-on-tomcat.git'
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
                     sh 'scp -o StrictHostKeyChecking=no target/java-tomcat-maven-example.war ubuntu@18.237.132.206:8080:/opt/tomcat/webapps'
    
               }
            }
        }
    }
   
}