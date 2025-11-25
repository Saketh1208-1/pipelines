// Jenkinsfile

pipeline {
    agent any

    // Define environment variables
    environment {
        PROJECT_NAME = 'Smart-Attendance-Management-System'
        GIT_REPO = 'https://github.com/Deekshitha-Y00/SCAM.git'
    }

    stages {
        // Stage 1: Build the Project
        stage('Build') {
            steps {
                script {
                    echo "Cloning the repository from ${GIT_REPO}"
                    // Clone the repository
                    git url: "${GIT_REPO}", branch: 'main'
                    echo "Repository cloned successfully"
                    // Add your build commands here (e.g., compile code, install dependencies)
                    // If it's a Java project, you can use Maven or Gradle to build it.
                    // Example for Maven:
                    // sh 'mvn clean install'
                }
            }
        }

        // Stage 2: Test the Project
        stage('Test') {
            steps {
                script {
                    echo "Running tests..."
                    // Add test commands here (e.g., run unit tests)
                    // For example, for a Java project using Maven:
                    // sh 'mvn test'
                    // Example for Node.js projects:
                    // sh 'npm install'
                    // sh 'npm test'
                }
            }
        }
    }

    // Post-actions after the pipeline finishes
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
