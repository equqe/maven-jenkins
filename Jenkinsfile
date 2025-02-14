pipeline {
    agent any

    tools {
        maven 'M3'
        jdk 'jdk'
    }

    environment {
        SONARQUBE_SCANNER = 'SonarQube'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/equqe/maven-jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv(SONARQUBE_SCANNER) {
                    sh 'mvn sonar:sonar \
                        -Dsonar.projectKey=maven-jenkins \
                        -Dsonar.host.url=http://localhost:9000 \
                        -Dsonar.login=sqa_5a6b1cfb8984d629415d23e040a39f465b1cfba4'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and analysis successful!'
        }
        failure {
            echo 'Build or analysis failed!'
        }
    }
}