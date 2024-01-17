pipeline {
    agent any
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
                withCredentials([usernamePassword(credentialsId: 'dockerid', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                 sh 'docker push praveenkumar2504/task:latest'
            }     

            }
        }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
