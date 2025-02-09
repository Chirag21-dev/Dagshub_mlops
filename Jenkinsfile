pipeline {
    agent any
    environment {
        DAGSHUB_MLFLOW_URL = "https://dagshub.com/Chirag21-dev/dagshub_mlops.mlflow"
        MLFLOW_TRACKING_USERNAME = "Chirag21-dev"
        MLFLOW_TRACKING_PASSWORD = credentials('Dagshub_mlops')
    }
    stages {
        stage('Clone Repository') {
            steps {
                // Clone Repository
                script {
                    echo 'Cloning DagsHub Repository...'
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Dagshub_mlops', url: 'https://dagshub.com/Chirag21-dev/dagshub_mlops.git']])
            }
        }
        }
        stage('Install the necessary Packages') {
            steps {
                // Install Packages
                script {
                    echo 'Install Python Packages...'
                    sh '''
                        python --version
                        pip install --break-system-packages -r requirements.txt >> req-output.txt
                    '''
                }
            }
        }
        stage('Train Model') {
            steps {
                // Train ML Model
                script {
                    echo 'Training ML Model ...'
                    sh 'python train.py'
                }
            }
        }
    }
}

