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
              bat 'docker build -t alpine2 -f Dockerfile .'
            }
        }
        stage('Tag Image') {
            steps {
                bat 'docker tag alpine2 sania021/alpine2'
            }
        }
        stage ('Push Image') {
            steps{
                bat ' docker push sania021/alpine2'
            }
        }
         stage('Run Image') {
           
            steps {
               bat 'docker run --name alpine21 -p 7720:80 -d alpine2'
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
