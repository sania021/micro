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
         stage('Run Image') {
           
            steps {
               bat 'docker run --name b11 -p 7701:80 -d nginx01'
            }
        }
         stage('exec Image') {
          
            steps {
               bat 'docker exec -it b11 /bin/bash'
                
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
