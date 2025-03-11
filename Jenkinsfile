pipeline {
    agent any

    environment {
        SRN = "PES2UG22CS532"
        REPO_URL = "https://github.com/shreyahegde26/PES2UG22CS532_Jenkins" // Replace with your actual repo URL
        FILE_NAME = "hello.cpp"
    }

    stages {
        stage('Create & Push .cpp File') {
            steps {
                script {
                    sh '''
                        echo "#include <iostream>\nusing namespace std;\nint main() {\n    cout << \"Hello, Jenkins Pipeline!\" << endl;\n    return 0;\n}" > $FILE_NAME
                        git init
                        git remote add origin $REPO_URL
                        git add $FILE_NAME
                        git commit -m "Added working C++ file"
                        git branch -M main
                        git push -u origin main
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh "g++ -o $SRN $FILE_NAME"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh "./$SRN"
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add deployment logic here
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
