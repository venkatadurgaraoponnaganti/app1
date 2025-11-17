pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/venkatadurgaraoponnaganti/app1'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m venv venv
                    source bin/venv/activate
		    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Docker Build & Run') {
            steps {
                sh '''
                    docker build -t app2 .
                    docker run -d -p 5000:5000 app2
                '''
            }
        }
    }
}


