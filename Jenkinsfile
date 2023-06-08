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
              bat 'docker build -t nginx01 -f Dockerfile .'
            }
        }
        stage('Tag Image') {
            steps {
                bat 'docker tag nginx01 sania021/nginx01'
            }
        }
        stage ('Push Image') {
            steps{
                bat ' docker push sania021/nginx01'
            }
        }
         stage('Run Image') {
           
            steps {
               bat 'docker run --name b23 -p 7700:80 -d nginx01'
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
