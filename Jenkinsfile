pipeline {
    agent any

    parameters {
        string(name: 'testUrl', defaultValue: 'https://youtube.com', description: 'Enter the URL for testing')
        choice(name: 'browser', choices: ['chrome', 'firefox'], description: 'Select the browser for testing')
        string(name: 'driversPath', defaultValue: 'C:\Users\rishi\Downloads\path_to_web_drivers', description: 'Path to WebDriver executables')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/RishitaChavan/selenium.git'
            }
        }

        stage('Build') {
            steps {
                dir('selenium-tests') {
                    bat 'mvn clean package -DdriversPath=%driversPath%'
                }
            }
        }

        stage('Test') {
            steps {
                dir('selenium-tests') {
                    bat "mvn test -DtestUrl=${params.testUrl} -Dbrowser=${params.browser} -Ddrivers=${params.driversPath}"
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up after execution'
        }
        success {
            echo 'Tests executed successfully'
        }
        failure {
            echo 'Tests failed! Check the logs.'
        }
    }
}
