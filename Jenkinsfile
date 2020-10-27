pipeline {
    agent any
    stages {
        stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
        } 
        stage('Upload to AWS') {
            steps {
                withAWS(region:'us-west-2', credentials:'aws-static') {
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-devops')
                }
            }
        }
        stage('Check Website') {
              steps {
                    sh 'curl -I "http://udacity-devops.s3-website-us-west-2.amazonaws.com/" 2>&1 | grep -w "200\\|301"'
              }
        } 

    }
}