pipeline {
    agent { 
                label 'Ubuntu_node'
            }
   
    stages {
        
        stage('Build application') {
            steps {
                sh 'mvn -f DockerTomcat/pom.xml clean package'
                
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