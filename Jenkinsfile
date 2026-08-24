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
                    echo "Checking index.html..."

                    tidy --doctype html5 -errors -q index.html

                    STATUS=$?

                    if [ $STATUS -eq 0 ]; then
                        echo "HTML validation successful!"
                    else
                        echo "HTML validation failed!"
                        exit $STATUS
                    fi
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Build successful!'
            }
        }
    }
}
