pipeline {
    agent none // No global agent, defined per stage
    stages {
        stage('Backend Build') {
            agent {
                docker {
                    image 'maven:3.8.1-adoptopenjdk-11' // Maven with OpenJDK 18
                }
            }
            steps {
                script {
                    // Verify Maven and Java versions
                    sh 'mvn -version'
                    sh 'java -version'
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

