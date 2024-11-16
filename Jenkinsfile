pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                echo 'Cloning the repository...'
                git branch: 'main', url: 'https://github.com/mvsanthi123/jenkins.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh '''
                    echo "your_password" | sudo -S apt-get update
                    echo "your_password" | sudo -S apt-get install -y python3.12-venv
                    python3 -m venv venv
                    . venv/bin/activate  # Activate the virtual environment
                    python3 -m pip install --upgrade pip
                    python3 -m pip install -r requirements
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh '''
                    . venv/bin/activate  # Ensure virtual environment is activated
                    pytest  # Run the tests with pytest
                '''
            }
        }
    }
}
