pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                git branch: 'main', url: 'https://github.com/mvsanthi123/jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                // Install virtualenv and create a virtual environment
                sh 'python3 -m pip install --user virtualenv' // Install virtualenv if necessary
                sh 'python3 -m venv venv' // Create a virtual environment
                // Activate virtual environment and install dependencies
                sh '. venv/bin/activate && pip install --upgrade pip'
                sh '. venv/bin/activate && pip install -r requirements.txt' 
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                // Run tests inside the virtual environment
                sh '. venv/bin/activate && pytest test_app.py'
            }
        }
    }
}
