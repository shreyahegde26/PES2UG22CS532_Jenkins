pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/shreyahegde26/PES2UG22CS532_Jenkins'
            }
        }

        stage('Create & Push .cpp File') {
            steps {
                script {
                    sh '''
                    set -e

                    # Create main.cpp
                    cat <<EOL > main.cpp
                    #include <iostream>
                    using namespace std;
                    int main() {
                        cout << "Hello, Jenkins Pipeline!" << endl;
                        return 0;
                    }
                    EOL

                    # Add, commit, and push the file
                    git add main.cpp
                    git commit -m "Added main.cpp via Jenkins"
                    git push origin main
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                sh 'g++ -o main main.cpp'
            }
        }

        stage('Test') {
            steps {
                sh './main'
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
