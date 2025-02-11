pipeline {
    agent any

    environment {
        SONARQUBE_URL = 'http://192.168.19.217:9000'
        SONARQUBE_TOKEN = credentials('sqp_eb1322b0cdc6fa2d2eb2373ed7bc4f3af246b450')
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/imtan666/test-webhook.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                    sonar-scanner \
                      -Dsonar.projectKey=your-project \
                      -Dsonar.sources=. \
                      -Dsonar.host.url=${SONARQUBE_URL} \
                      -Dsonar.login=${SONARQUBE_TOKEN}
                    '''
                }
            }
        }
    }
}
