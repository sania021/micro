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
