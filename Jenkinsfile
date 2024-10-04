pipeline {
    agent any
   
    stages {
        
        stage('Build application') {
            steps {
                bat 'mvn -f pom.xml clean package'
                
            }
            post {
                success {
                    echo 'Started arhiving war file'
                    archiveArtifacts artifacts: '**/*.war'
                    echo 'finished arhiving war file'
                }
            }
        }

        stage('Create Tomcat Docker Image') {
            steps{
                bat 'docker build . -t tomcatsamplewebapp:${BUILD_NUMBER}' 
            }

        }
            
    }
}