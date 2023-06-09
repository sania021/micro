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
              bat 'docker build -t node_doc:1 -f Dockerfile1 .'
            }
        }
        stage('Tag Image') {
            steps {
                bat 'docker tag node_doc:1 sania021/node_doc:1'
            }
        }
        stage ('Push Image') {
            steps{
                bat ' docker push sania021/node_doc:1'
            }
        }
        stage('Run Image') {
           
            steps {
               bat 'docker run --name s19 -p 7785:3070 -d node_doc:1'
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
