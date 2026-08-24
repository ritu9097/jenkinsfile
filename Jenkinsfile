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

                    tidy -html5 -errors -q index.html

                    if [ $? -eq 0 ]; then
                        echo "HTML validation successful!"
                    else
                        echo "HTML validation failed!"
                        exit 1
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
