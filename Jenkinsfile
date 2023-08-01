pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the GitHub repository
                git 'https://github.com/namgungu/nkw.git'
            }
        }
        stage('Build') {
            steps {
                // No specific build steps for now, as we are using Kubernetes YAML files
            }
        }
        stage('Test') {
            steps {
                // Assuming you are using Jest for testing in a Node.js project
                sh 'npm install' // Install dependencies
                sh 'npm test'    // Run tests with npm
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                // Assuming you have Kubernetes configured in your Jenkins environment
                sh 'kubectl apply -f hpa-nginx-deploy.yaml'
                sh 'kubectl apply -f hpa-tomcat-deploy.yaml'
            }
        }
    }

    // Post-build actions (optional)
    post {
        success {
            // Actions to be performed after a successful build
            // For example, notify team members, publish artifacts, etc.
        }
        failure {
            // Actions to be performed after a failed build
            // For example, send an alert, cleanup, etc.
        }
    }
}
