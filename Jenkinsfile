pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning the repository...'
                git branch: 'main', url: 'https://github.com/mvsanthi123/jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh 'python3 -m pip install --user -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh 'python3 -m pytest test_app.py'
            }
        }
    }
}
