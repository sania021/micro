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
              bat 'docker build -t node_doc -f Dockerfile1 .'
            }
        }
        stage('Tag Image') {
            steps {
                bat 'docker tag node_doc sania021/node_doc'
            }
        }
        stage ('Push Image') {
            steps{
                bat ' docker push sania021/node_doc'
            }
        }
        stage('Run Image') {
           
            steps {
               bat 'docker run --name s11 -it --rm node_doc'
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
