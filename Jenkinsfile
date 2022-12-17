#!groovy
pipeline{
    agent any
    tools{
        maven "maven_3.8.6"
    }
    stages{
        stage("clone repo from git "){
            steps{
                git 'https://github.com/GlobeDaBoarder/WebApp2.git'
            }
        }
        stage("build"){
            steps{
                sh "mvn clean install"
            }
        }
        stage("deploy"){
            steps{
              sshagent(['ssh_jenkins']) {
                  sh "sshpass -p root scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/WebApp2/target/WebApp2-1.0-SNAPSHOT.war root@192.168.100.5:/opt/tomcat/apache-tomcat-10.0.27/webapps/page.war"
                }
            }
        }
    }
}
