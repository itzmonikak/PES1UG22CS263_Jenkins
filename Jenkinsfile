pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/itzmonikak/PES1UG22CS263_Jenkins.git'
        BRANCH = 'main'
        BINARY_NAME = 'hello'
        SOURCE_FILE = 'main/hello.cpp'  // <-- FIXED PATH
    }

    stages {
        stage('Clean Workspace') {
            steps {
                sh 'exit 1'  
                //deleteDir()
            }
        }

        stage('Clone Repository') {
            steps {
                git branch: BRANCH, url: REPO_URL
            }
        }

        stage('Debug') {
            steps {
                echo "### Checking files in workspace ###"
                sh 'pwd'   // Print current directory
                sh 'ls -R' // List all files to verify hello.cpp exists
            }
        }

        stage('Compile') {
            steps {
                sh 'g++ -o ${BINARY_NAME} ${SOURCE_FILE}'
            }
        }

        stage('Run Executable') {
            steps {
                sh './${BINARY_NAME}'
            }
        }
    }

    post {
        success {
            echo "✅ Build and execution completed successfully!"
        }
        failure {
            echo "❌ Build failed! Check errors."
        }
    }
}
