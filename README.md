pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {
        stage('Welcome') {
            steps {
                echo 'Welcome to Jenkins Pipeline'
            }
        }

        stage('Git Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/jashuu5/MavenJavaFinal.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Complete') {
            steps {
                echo 'Maven project built successfully!'
            }
        }
    }
}
