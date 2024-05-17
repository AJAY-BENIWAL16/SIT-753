
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Building the code using Maven
                    sh 'mvn clean package'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    // Running unit and integration tests
                    sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    // Code analysis using SonarQube
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    // Security scan using OWASP Dependency-Check
                    sh 'mvn dependency-check:check'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    // Deploying to staging server
                    sh 'aws deploy create-deployment ...' // Adjust with actual deployment command
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    // Running integration tests on staging
                    sh 'run-integration-tests.sh'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    // Deploying to production server
                    sh 'aws deploy create-deployment ...' // Adjust with actual deployment command
                }
            }
        }
    }

    post {
        always {
            emailext (
                to: 'developer@example.com',
                subject: "Pipeline ${currentBuild.fullDisplayName}",
                body: """<p>Build ${currentBuild.fullDisplayName} completed</p>
                         <p>Status: ${currentBuild.result}</p>""",
                attachLog: true
            )
        }
    }
}
