@Library("shared-library") _
pipeline {
    agent { label "vinod" }

    stages {
        stage('shared'){
            steps{
                script{
                    hello()
                       
                }
            }
        }
        stage('Code') {
            steps {
               
                clone("https://github.com/Navneet2497/django-notes-app.git","main")
                
            }
        }
        stage('Build') {
            steps {
                script {
                    docker_hub("notes-app","latest","navneet2497")
                }
            }
        }
        stage('Pushing to docker hub') {
            steps {
                script {
                    docker_push("notes-app","latest","navneet2497")
                }
                
            }
        }
        stage('Deploy') {
            steps {
                echo 'This is a deployment phase'
                sh "docker compose up -d"
            }
        }
        
    }
}
