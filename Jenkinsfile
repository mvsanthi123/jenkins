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
                    python3 -m venv venv
                    source venv/bin/activate
                    python3 -m pip install --upgrade pip
                    python3 -m pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                // Add your test commands here, for example:
                // sh 'pytest'
            }
        }
    }
}
