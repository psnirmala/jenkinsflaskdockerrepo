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
                script{
                  echo "========executing settingup environment========"
                  bat 'docker build -t flask-jenkins-image:latest .'
                }
            }
        }
        
        stage("Deploy Docker Container"){
            steps{
                script{
                bat 'FOR /F "tokens=*" %i IN (\'docker ps -aq --filter "name= flask-container"\' ) DO docker rm -f %i'
                bat 'docker run -d -p 5000:5000 --name flask-container flask-jenkins-image:latest'
                }
            }
        }
    }
}    
    