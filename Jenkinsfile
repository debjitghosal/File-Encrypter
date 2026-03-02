pipeline {
    agent {
        label 'docker-agent'
    }

    stages {

        stage('Build') {
            steps {
                sh '''
                echo "Building Java project on Agent..."
                cd "Password Protection"
                mkdir -p build
                javac -d build src/*.java
                echo "Build successful"
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                echo "Running verification on Agent..."
                cd "Password Protection"
                ls build
                echo "Test stage complete"
                '''
            }
        }

        stage('Package') {
            steps {
                sh '''
                echo "Packaging application on Agent..."
                cd "Password Protection"
                jar cf FileEncrypter.jar -C build .
                echo "Artifact created successfully"
                '''
            }
        }
    }

    post {
        success {
            echo "Distributed CI/CD Pipeline completed successfully on docker-agent!"
        }
        failure {
            echo "Pipeline failed on docker-agent!"
        }
    }
}
