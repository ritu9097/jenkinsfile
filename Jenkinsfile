pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check HTML') {
            steps {
                sh '''
                    echo "================================="
                    echo "Checking index.html"
                    echo "================================="

                    if [ ! -f index.html ]; then
                        echo "ERROR: index.html not found!"
                        exit 1
                    fi

                    echo "Installing HTML validator..."

                    npm install --no-save html-validate

                    echo "Running HTML validation..."

                    npx html-validate index.html

                    echo "HTML validation completed successfully!"
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'HTML validation passed!'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: index.html is valid!'
        }

        failure {
            echo 'FAILURE: HTML validation failed!'
        }
    }
}
