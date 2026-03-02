pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh '''
                echo "Building Java project..."
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
                echo "Running basic verification..."
                cd "Password Protection"
                ls build
                echo "Test stage complete"
                '''
            }
        }

        stage('Package') {
            steps {
                sh '''
                echo "Packaging application..."
                cd "Password Protection"
                jar cf FileEncrypter.jar -C build .
                echo "Artifact created"
                '''
            }
        }
    }

    post {
        success {
            echo "CI/CD Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
