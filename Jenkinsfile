pipeline {
    agent none // No global agent, defined per stage
    stages {
        stage('Backend Build') {
            agent {
                docker {
                    image 'maven:3.8.7-openjdk-18-slim' // Maven with OpenJDK 18
                }
            }
            steps {
                script {
                    // Verify Maven and Java versions
                    sh 'mvn -version'
                    sh 'java -version'

                    // Run backend build (example: compile a Maven project)
                    sh 'mvn clean install'
                }
            }
        }

        stage('Frontend Build') {
            agent {
                docker {
                    image 'node:16-alpine' // Node.js 16 with Alpine
                }
            }
            steps {
                script {
                    // Verify Node.js and npm versions
                    sh 'node --version'
                    sh 'npm --version'

                    // Install frontend dependencies and build (example: React project)
                    sh '''
                    npm install
                    npm run build
                    '''
                }
            }
        }
    }
}

