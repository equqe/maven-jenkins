pipeline {
    agent any

    tools {
        maven 'M3'
        jdk 'jdk'
    }

    environment {
        PATH = "C:\\Windows\\System32;${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/equqe/maven-jenkins.git' // ссылка на репозиторий
            }
        }

        stage('Build') {
            steps {
                dir('demo') {
                    bat 'mvn clean install'
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('maven-jenkins') { // имя, указанное в настройках Jenkins
                    dir('demo') {
                        bat 'mvn clean verify sonar:sonar \
                            -Dsonar.projectKey=maven-jenkins \
                            -Dsonar.projectName=maven-jenkins'
                    }
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