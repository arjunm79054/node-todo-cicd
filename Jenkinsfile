peline {
    agent any
    
    stages {
        stage ('git checkout scm'){
            steps {
            
            checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/arjunm79054/node-todo-cicd']])
        }
        }       
        
        stage('docker build image'){
            steps{
                sh 'docker build . -t devops-automation-dev:latest'
            }
        }
        
        stage('docker image push to dockerhub'){
            steps{
                withCredentials([string(credentialsId: 'username', variable: 'username'), string(credentialsId: 'dockerhubpassword', variable: 'dockerhubpassword')]) {
                sh 'docker login -u ${username} -p ${dockerhubpassword}'
                sh 'docker image tag devops-automation-dev:latest arjunm7954/node-app'
                sh 'docker push arjunm7954/node-app:latest'
                } 
            }
        }
    
    }

}
