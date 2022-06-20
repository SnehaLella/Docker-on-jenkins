pipeline{

    agent any 
	
	 tools {  
	  maven 'Maven 3.6.0'  
	}
    
    stages{
	
        stage('scm clone'){
            steps{
            git branch: 'main', 
			credentialsId: 'SnehaLellasneha-9121806763', 
			url: 'https://github.com/SnehaLella/Docker-on-jenkins.git'
            }
        }
        stage('build image'){
            steps{
                sh "docker build . -t hello-world:${BUILD_NUMBER}"
            }
        }
		
		stage('Deploy to ECR'){
            steps{
               script{
			   docker.withRegistry(
			   'https://289987706411.dkr.ecr.us-east-1.amazonaws.com',
			   'ecr: us-east-1:289987706411'){
			   def myImage = docker.build('jenkins')
			   myImage.push('v2')
			   
            }
        }
        
        
    }
}
