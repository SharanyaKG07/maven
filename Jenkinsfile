pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('CHECKOUT') {
            steps {
                git 'https://github.com/SharanyaKG07/maven.git'
            }
        }

        stage('Build') {
            steps {
                dir('demo') {
                    bat 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                dir('demo') {
                    bat 'mvn test'
                }
            }
        }
    }

    post {
        success {
            mail to: 'vvce23ise0118@vvce.ac.in',
                 subject: "SUCCESS: Jenkins Build",
                 body: "Build succeeded for ${env.JOB_NAME} #${env.BUILD_NUMBER}"
        }

        failure {
            mail to: 'your_email@gmail.com',
                 subject: "FAILED: Jenkins Build",
                 body: "Build failed for ${env.JOB_NAME} #${env.BUILD_NUMBER}"
        }
    }
}
