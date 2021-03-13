pipeline {
    agent any 
    stages {
        stage('Clean & Compile') { 
            steps {
		sh "printenv"
                sh "mvn clean compile"
            }
        }
        stage('Test') { 
            steps {
                sh "mvn test "
            }
        }
        stage('Package') {
            steps {
                sh "mvn package "
            }
        }
        
        stage('Archiving') {
            steps {
                archiveArtifacts '**/target/*.jar'
            }
        }
    }
}
