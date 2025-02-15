pipeline {
    agent none 
    environment {
        ACCESS_CREDENTIALS = credentials('latest-jfrog-creds')
    }
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
            agent{ label 'node-slave'}
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('Build & Deploy') {
            agent { label 'node-slave' }
            steps {
                sh 'mkdir -p ~/.m2'
                sh '''
                    echo "
                    <settings>
                        <servers>
                            <server>
                                <id>test1hello-world-war-libs-release</id>
                                <username>$ACCESS_CREDENTIALS_USR</username>
                                <password>$ACCESS_CREDENTIALS_PSW</password>
                            </server>    
                        </servers>
                    </settings>
                    " > ~/.m2/settings.xml
                '''
                sh 'mvn clean deploy'
            }
        }        
    }
}
