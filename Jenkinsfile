pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')   // every 2 minutes (for testing)
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/nithyashreek301-max/jenkins-scm-lab.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building application..."
                sh 'echo "Build completed" > build.txt'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'echo "All tests passed" > test.txt'
            }
        }

        stage('Artifacts') {
            steps {
                echo "Archiving artifacts..."
                archiveArtifacts artifacts: '*.txt', fingerprint: true
            }
        }

        stage('Fingerprinting') {
            steps {
                echo "Generating fingerprint..."
                fingerprint '*.txt'
            }
        }
    }

    post {
        always {
            echo "Build finished"
        }
        success {
            echo "SUCCESS"
        }
        failure {
            echo "FAILED"
        }
    }
}
