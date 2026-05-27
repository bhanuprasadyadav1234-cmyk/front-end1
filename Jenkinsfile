pipeline {
    agent any

    tools {
        nodejs 'node20'
    }

    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
        S3_BUCKET = 'your-s3-bucket-name'
    }

    stages {

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Frontend') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to S3') {
            steps {
                sh '''
                aws s3 sync build/ s3://$S3_BUCKET --delete
                '''
            }
        }
    }
}
