pipeline {
    agent any
    
    environment {
        VENV_DIR = 'venv'
    }
    
    stages {
        stage('Checkout SCM') {
            steps {
                echo "Cloning the repository..."
                git branch: 'main', url: 'https://github.com/mvsanthi123/jenkins.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh '''
                    python3 -m venv ${VENV_DIR}
                    . ${VENV_DIR}/bin/activate
                    python3 -m pip install --upgrade pip
                    python3 -m pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh '''
                    . ${VENV_DIR}/bin/activate
                    pytest
                '''
            }
        }
        
        stage('Extract Data from app.py and Display Output') {
            steps {
                script {
                    // Assuming 'app.py' contains some output-producing code
                    def appContent = readFile('app.py')
                    
                    // For example, if app.py has a function `get_output()`, call it
                    // If it's not a function, you could execute it or just process the content
                    // Here's an example assuming `app.py` has a function `get_output()`
                    
                    def output = sh(script: 'python3 -c "from app import get_output; print(get_output())"', returnStdout: true).trim()
                    
                    echo "Output from app.py: ${output}"
                }
            }
        }
    }
}
