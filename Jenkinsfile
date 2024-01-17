pipeline {
    agent any
        environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerid')
        dockerHubUser='praveenkumar2504'
        dockerHubPassword='Praveen@2504'
    }
    
    stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/Praveen-Dev0ps/node-todo-cicd-master-jenkins.git' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t praveenkumar2504/task:latest'
            }
        }
        stage('Push'){
            steps{
                
        	     sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                 sh 'docker push praveenkumar2504/task:latest'

            }
        }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
