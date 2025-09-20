@Library('code_fetch') _

pipeline {
    agent { label 'ashish-agent' }

    stages {
        stage('code') {
            steps {
                script {
                    code_fetch("https://github.com/mashish1010/ashish-django-notes-app.git", "main")
                }
            }
        }

        stage('build') {
            steps {
                script {
                    Docker_build("latest", "notes-app", "ashishmathur1991")
                }
            }
        }

        stage('push to docker hub') {
            steps {
                script {
                    Docker_push("notes-app", "latest")
                }
            }
        }

        stage('deploy') {
            steps {
                echo "This is Deploying codes"
                sh "docker compose up -d"
            }
        }
    }
}
