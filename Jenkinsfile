pipeline {
    agent any
    options {
        timeout(time: 1, unit: 'HOURS')
        skipStagesAfterUnstable()
    }
    stages {
        stage('Clean & Compile') { 
            steps {
                sh "mvn clean compile"
            }
        }
        stage('Package') {
            steps {
                sh "mvn package "
            }
        }
        stage('Dockerize') {
            steps {
                sh "docker build -i dreambeam/springboot:${BUILD_ID} . "
            }
        }
        
        stage('Deploy') {
            steps {
                sh "docker run -d -p 8081:8080 dreambeam/springboot:${BUILD_ID} "
            }
        } 
     
        stage('Archiving') {
            steps {
                archiveArtifacts '**/target/*.jar'
            }
        }
    }
}
