pipeline {
    agent any
    stages {
        stage('Upload to AWS') {
            steps {
                withAWS(region:'us-west-2', credentials:'aws-static') {
                    s3upload(file:'index.html', bucket:'udacity-devops', path:'/index.html')
                }
            }
        }
    }
}