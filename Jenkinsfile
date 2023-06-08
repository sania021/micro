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
              bat 'docker build -t ubuntu -f Dockerfile .'
            }
        }
         stage('Tag Image') {
           
            steps {
               bat 'docker tag ubuntu sania021/ubuntu'
            }
        }
         stage('Push Image') {
          
            steps {
               bat 'docker login -u sania021 -p Sania@7866'
                bat 'docker push sania021/ubuntu'
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
