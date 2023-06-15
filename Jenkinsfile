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
         stage('push image') {
            steps {
              bat 'sudo docker login -u sania021 -p Sania@7866'
                bat 'sudo docker push sania021/nginx01'
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
