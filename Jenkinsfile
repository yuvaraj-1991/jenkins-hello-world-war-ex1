pipeline {
    agent none 
    stages {
        stage ('Checkout') {
            agent { label 'node-slave' }
            steps {
                sh 'echo Git Checkout'
            }
        }
    }
}
