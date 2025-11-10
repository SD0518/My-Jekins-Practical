Groovy
// This is the Jenkinsfile
pipeline {
    // Use a Docker container with Maven and JDK 11 as the build environment
    agent {
        docker { image 'maven:3.8-jdk-11' }
    }

    // Define the stages of the pipeline
    stages {
        stage('Compile') {
            steps {
                // Run the Maven compile command
                sh 'mvn compile'
            }
        }
        stage('Build') {
            steps {
                // Build the .jar or .war file
                sh 'mvn package'
            }
        }
        stage('Test') {
            steps {
                // Run all automated tests
                sh 'mvn test'
            }
        }
    }

    // Define actions that run after the pipeline finishes
    post {
        always {
            // Archive the build artifacts (the packaged application)
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs.'
        }
    }
}
