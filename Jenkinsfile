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
                withCredentials([usernamePassword(credentialsId:"docker-cred",passwordVariable:"dockercredPass",usernameVariable:"dockercredUser")]){
                sh "docker tag notes-app ${env.dockercredUser}/notes-app:latest"
                sh "docker login -u ${env.dockercredUser} -p ${env.dockercredPass}"
                sh "docker push ${env.dockercredUser}/notes-app:latest"
                }
            }
        }

        stage("Deploy"){
            steps{
                echo "Deploy"
                sh "docker run -d -p 8000:8000 siddharth20/notes-app:latest"
            }
        }
    }
}
