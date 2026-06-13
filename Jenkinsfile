pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting Source Code'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }
}