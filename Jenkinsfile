pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                echo "========executing checkout========"
                checkout scm
            }
        }            
        stage("build docker image"){
            steps{
                  echo "========executing settingup environment========"
                  bat 'docker build -t flask-jenkins-image:latest .'
            }
        }
        
        stage("Deploy Docker Container"){
            steps{
                bat 'docker stop flask-container || true'
                bat 'docker rm flask-container || true'
                bat 'docker run -d -p 5000:5000 --name flask-container flask-jenkins-image:latest'
            }
        }
    }
}    
    