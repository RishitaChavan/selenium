pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the Selenium project...'
            }
        }
        stage('Run Selenium Tests') {
            steps {
                dir('selenium-tests') {  // Change 'selenium-tests' to your actual test folder
                    sh 'python test_script.py'
                }
            }
        }
    }
}
