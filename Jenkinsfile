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
    }
}
