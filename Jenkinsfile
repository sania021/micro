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
              sh 'docker build -t ubuntu_jenkins -f Dockerfile .'
            }
        }
         stage('Tag Image') {
           
            steps {
               sh 'docker tag ubuntu_jenkins:latest sania021/ubuntu:latest'
            }
        }
         stage('Push Image') {
          
            steps {
               sh 'docker login -u sania021 -p Sania@7866'
                sh 'docker push sania021/ubuntu_jenkins:latest'
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
