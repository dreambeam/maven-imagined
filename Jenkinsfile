pipeline {
    agent any 
    stages {
        stage('Clean & Clone repository') { 
            steps {
                sh "rm -rf maven-imagined"
                sh "git clone https://github.com/dreambeam/maven-imagined.git"
                sh "mvn clean -f maven-imagined"
            }
        }
        stage('Test') { 
            steps {
                sh "mvn test -f maven-imagined"
            }
        }
        stage('Deploy') { 
            steps {
                sh "mvn package -f maven-imagined"
            }
        }
    }
}
