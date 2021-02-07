pipeline {
    agent none
    stages {
        stage('Test on QA Agent') {
            agent { label 'testagent' }
            steps {
                checkout scm 
                sh 'mvn test'
            }
        }
        stage('Build APP on build agent') {
            agent { label 'buildagent' }
            steps {
                checkout scm
                sh 'mvn install -DskipTests'
                stash includes: '**/target/*.war', name: 'app' 
            }
        }
    }
}