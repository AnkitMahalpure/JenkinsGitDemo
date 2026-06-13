pipeline {

    agent any

    parameters {
        choice(
            name: 'ENV',
            choices: ['DEV', 'QA', 'PROD'],
            description: 'Deployment Environment'
        )
    }

    stages {

        stage('Info') {
            steps {
                echo "Build Number: ${env.BUILD_NUMBER}"
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENV}"
            }
        }
    }

    post {
        success {
            echo 'Build Successful'
        }

        failure {
            echo 'Build Failed'
        }

        always {
            echo 'Pipeline Finished'
        }
    }
}