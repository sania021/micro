pipeline {
    agent any
    stages {
        stage('check out') {
            steps {
              checkout scm
            }
        }
         stage('docker compose stop') {
            steps {
                bat 'docker-compose down'
            }
        }
         stage('docker compose start') {
            steps {
              bat 'docker-compose up -d'
            }
        }
        stage('tag  image') {
            steps {
              bat 'docker tag nginx sania021/nginx'
            }
        }
         stage('push image') {
            steps {
              bat 'docker login -u sania021 -p Sania@7866'
                bat 'docker push sania021/nginx'
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
