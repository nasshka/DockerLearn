pipeline {
    agent any
   
    stages {
        
        stage('Build application') {
            steps {
                bat 'mvn -f pom.xml clean package'
                
            }
            post {
                success {
                    echo 'Archiving the artefact'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }

        stage('Create Tomcat Docker Image') {
            steps{
                sh 'docker build . -t tomcatsamplewebapp:${env.BUILD_ID}' 
            }

        }
            
    }
}