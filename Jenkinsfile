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
        stage('Dockerize') {
            steps {
                sh "docker build -t dreambeam/springboot:${BUILD_ID} . "
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
