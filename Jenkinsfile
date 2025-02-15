pipeline {
    agent none 
    stages {
        stage ('Checkout') {
            agent { label 'node-slave' }
            steps {
                sh 'echo Git Checkout'
            }
        }
        stage ('Check for JDK Version') {
            agent { label 'node-slave' } 
            steps {
                sh 'java --version'
                sh 'mvn --version'
            }
        }
        stage ('Package') {
            agent { label 'node-slave' }
            steps {
                sh 'pwd'
                sh 'ls'
                sh 'mvn clean package'         
                sh 'ls'
            }
        }
        stage ('Deploy on Tomcat') {
            agent { label 'node-slave' } 
            steps {
                sh 'cd /home/ubuntu/jenkins/workspace/New-test1/target'  
                sh 'sudo cp hello-world-war-${BUILD_NUMBER} /opt/tomcat/apache-tomcat-10.1.34/webapps/'
                sh 'sudo bash /opt/tomcat/apache-tomcat-10.1.34/bin/.stop.sh'
                sh 'sudo bash /opt/tomcat/apache-tomcat-10.1.34/bin/.start.sh'
            }
        }
    }
}
