pipeline {
    
    agent any

    stages{

        stage("Checkout SCM"){
            steps{
                echo "Checkout SCM"
                git url: "https://github.com/siddharth201983/django-notes-app.git", branch: "main"
            }
        }

        stage("Build"){
            steps{
                echo "Build"
                sh "docker build -t notes-app ."
            }
        }

        stage("Push to Dockerhub"){
            steps{
                echo "Push to Dockerhub"
            }
        }

        stage("Deploy"){
            steps{
                echo "Deploy"
            }
        }
    }
}
