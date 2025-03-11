pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the application...'
                    sh 'g++ -o PES2UG22CS532-1 main.cpp'  // Compile C++ file
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Testing the application...'
                    sh './PES2UG22CS532-1'  // Run compiled C++ file
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying application...'
                }
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed!'
        }
    }
}
