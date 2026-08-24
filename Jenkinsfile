pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ritu9097/jenkinsfile.git'
            }
        }

        stage('Check HTML') {
            steps {
                sh '''
                    echo "Checking HTML file..."

                    tidy -errors -q index.html

                    if [ $? -eq 0 ]; then
                        echo "HTML is valid!"
                    else
                        echo "HTML has errors!"
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
