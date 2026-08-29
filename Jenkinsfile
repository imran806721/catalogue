pipeline {
    agent {
        node {
            label 'ROBOSHOP'
        }
    }

    options {
        disableConcurrentBuilds()
        timeout(time: 15, unit: 'MINUTES')
    }

    stages {
        stage('Read version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    def appVersion = packageJson.version

                    echo "The application version is: ${appVersion}"
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh """
                        echo "Building"
                    """
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh '''
                        echo "Testing"
                    '''
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh '''
                        echo "Deploying"
                    '''
                }
            }
        }
    }

    post {
        always {
            echo 'I will always say Hello again!'
        }

        success {
            echo 'I will run when success'
        }

        failure {
            echo 'I will Run when it is failed'
        }
    }
}
