pipeline {
    agent any
    stages {
        stage('check out') {
            steps {
              checkout scm
            }
        }
         stage('Build Image') {
            steps {
              bat 'docker build -t node1 -f Dockerfile1 .'
            }
        }
        stage('Tag Image') {
            steps {
                bat 'docker tag node1 sania021/node1'
            }
        }
        stage ('Push Image') {
            steps{
                bat ' docker push sania021/node1'
            }
        }
        stage('Run Image') {
           
            steps {
               bat 'docker run --name node_con -p 7701:80 -d node1'
            }
        }
    }
    post { 
        aborted { 
            echo 'ABORTED'
        }
         success { 
            echo 'SUCCESS'
        }
         failure { 
            echo 'FAILURE'
        }
        changed { 
            echo 'FAILURE'
        }
    }
    
}
