pipeline {
    agent { 
                label 'Ubuntu_node'
            }
   
    stages {
        
        stage('Build application') {
            steps {
                sh 'mvn clean package'
                
            }
            post {
                success {
                    echo 'Archiving the artefact'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Push app to Server'){
            steps {
                timeout(time:5, unit:'DAYS'){ 
                    input message: 'Approve for deployement?'    
                }
            
                build job: 'pushWARtoTomcat'    
                
            }
            
        }
            
    }
}