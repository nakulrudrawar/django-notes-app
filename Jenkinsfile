@Library('shared-lib') _ 
pipeline {
    agent {label "a1"}
    stages {
        stage("Message"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code') {
            steps {
                script{
                    cloneRepo("https://github.com/nakulrudrawar/django-notes-app.git","main")
                }
            }
        }
        stage('Build') {
            steps {
               script{
                   docker_build("nakulrudrawar","django_app","latest")
               }
            }
        }
        stage('Push images to Docker Hub') {
            steps {
                script{
                    docker_build("nakulrudrawar","django_app","latest")
                }
            }
        }
        stage('Deploy') {
            steps {
                  echo 'THis stage deploy code'
  sh "docker compose down && docker compose up -d"
            }
        }
    }
}
