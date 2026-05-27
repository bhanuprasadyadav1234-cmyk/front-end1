pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
        S3_BUCKET = 'frontend-deploy-bucket-123'
    }

    stages {

        stage('Deploy Static Website') {
            steps {
                sh '''
                aws s3 sync . s3://$S3_BUCKET --delete \
                --exclude ".git/*" \
                --exclude "Jenkinsfile"
                '''
            }
        }
    }
}
