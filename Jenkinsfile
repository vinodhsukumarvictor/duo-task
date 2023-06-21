pipeline {
    agent any

    stages {
         
        stage('Build')   {
             steps {
                 sh 'docker build -t duo-task:v1 .'
             }
         }
         
        stage('run containers') {
             steps {
                sh '''
                docker network inspect duotask-net && sleep 1 || docker network create duetask-net
                docker run -d -p 80:5500 --network duotask-net --name duo-task duo-task:v1
                '''
             }
             
         }

    }
}
