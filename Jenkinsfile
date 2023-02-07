pipeline {
    agent any
    environment {
        PATH = "/usr/share/apache-maven/bin:$PATH"
    }
    stages {
        stage("hello"){
            steps{
                git 'https://github.com/chaitanya2616/ravdy-hello-world.git'
            }
        }
        stage("build"){
            steps{
                sh "mvn clean install"
            }
        }
        stage("deploy"){
            steps{
              sshagent(['deploy_user']) {
               sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@43.206.222.75:/opt/apache-tomcat-8.5.85/webapps"
              }
            }
        }
    }
}
