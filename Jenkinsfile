pipeline {
    agent {
        node {
            label 'ROBOSHOP'
        }
    }
    environment {
        def appVersion = ""
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
                    appVersion = packageJson.version

                    echo "The application version is: ${appVersion}"
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh """
                        npm install
                    """
                }
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    sh """
                       docker build -t catalogue:${appVersion} .
                    """
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
