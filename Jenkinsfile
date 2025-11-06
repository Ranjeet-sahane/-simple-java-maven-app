pipeline {

    agent any

    tools {
        maven 'M3'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Ranjeet-sahane/-simple-java-maven-app.git'
            }
        }

        stage('Build Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-user',
                        url: 'http://http://3.95.56.164:8081'
                    )
                ],
                war: 'target/*.war'
            }
        }
    }
}

