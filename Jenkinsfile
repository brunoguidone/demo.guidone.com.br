pipeline {
    agent none
    stages {
        stage('Test on QA Agent') {
            agent { label 'linux-test-agent' }
            steps {
                checkout scm 
                sh 'mvn test'
            }
        }
        stage('Build APP on build-agent') {
            agent { label 'linux-build-agent' }
            steps {
                checkout scm
                sh 'mvn build'
                stash includes: '**/target/*.war', name: 'app' 
            }
        }
    }
}