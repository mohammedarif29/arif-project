pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/mohammedarif29/arif-project.git'
                }
            }
        }
        stage('UNIT testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn test'
                }
            }
        }
        stage('Integration testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn verify -DskipUnitTests'
                }
            }
        }
        stage('Maven build'){
            
            steps{
                
                script{
                    
                    sh 'mvn clean install'
                }
            }
        }
        stage('upload jar to nexus'){

            steps{
                
                script{
                    nexusArtifactUploader artifacts: [[artifactId: 'spring-boot-starter-parent', classifier: '', file: 'var/lib/uber.jar', type: 'jar']], credentialsId: 'fc77ba4d-c576-43f5-9bc1-7a5320fbfbc0', groupId: 'com.example', nexusUrl: '192.168.0.16:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'arif-project-release', version: '1.0.0'
                }
            }
        }
    }
}    
