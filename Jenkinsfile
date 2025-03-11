pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/shreyahegde26/PES2UG22CS532_Jenkins'
            }
        }

        stage('Create & Push .cpp File') {
            steps {
                script {
                    sh '''
                    # Ensure any previous failures don't affect the pipeline
                    set -e

                    # Create the C++ file
                    cat <<EOL > main.cpp
                    #include <iostream>
                    using namespace std;
                    int main() {
                        cout << "Hello, Jenkins Pipeline!" << endl;
                        return 0;
                    }
                    EOL

                    # Initialize Git if not already initialized
                    [ ! -d ".git" ] && git init

                    # Add remote only if it doesn't exist
                    git remote | grep origin || git remote add origin https://github.com/shreyahegde26/PES2UG22CS532_Jenkins

                    # Add, commit, and push changes
                    git add main.cpp
                    git commit -m "Added main.cpp via Jenkins"
                    git push origin main
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh '''
                    # Compile the C++ file
                    g++ -o main main.cpp
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh '''
                    # Run the compiled program
                    ./main
                    '''
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Deployment step (Modify as needed)"
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for errors.'
        }
    }
}
