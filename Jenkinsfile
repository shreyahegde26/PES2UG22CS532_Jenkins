
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out code from GitHub repository
                git url: 'https://github.com/simrandas04/PES2UG22CS554_Jenkins.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                // Example build step (for C++ project)
                echo 'Building the C++ project...'
                sh 'g++ -o my_program my_program.cpp'
            }
        }

        stage('Test') {
            steps {
                // Example test step (you can replace it with actual test commands)
                echo 'Running tests...'
                sh './run-tests.sh'  // Replace with your test script
            }
        }

        stage('Deploy') {
            steps {
                // Example deploy step (you can replace it with your actual deployment commands)
                echo 'Deploying the application...'
                sh './deploy.sh'  // Replace with your deployment script
            }
        }
    }

    post {
        failure {
            // Post condition for when the pipeline fails
            echo 'Pipeline failed'
        }
    }
}
