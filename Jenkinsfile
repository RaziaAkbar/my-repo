pipeline {
    agent any

    stages {
        stage('dev') {
            steps {
                // Checkout your source code from version control
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build your project (compile, package, etc.)
                sh 'mvn clean package' // Replace with your build command
            }
        }

        stage('Unit Tests') {
            steps {
                // Run unit tests
                sh 'mvn test' // Replace with your unit test command
            }
        }

        stage('SonarQube Analysis') {
            steps {
                // Execute SonarQube analysis using the SonarQube Scanner
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar' // Replace with your SonarQube analysis command
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy your application (if applicable)
                // sh '...'
            }
        }
    }

    post {
        success {
            // This block executes if the pipeline succeeds
            echo 'Pipeline succeeded!'
        }

        failure {
            // This block executes if the pipeline fails
            echo 'Pipeline failed!'
        }
    }
}
