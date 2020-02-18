pipeline {
    agent any
    stages {
       stage('Lint HTML') {
             steps {
                 echo 'hello world'
                 script {tidy -q -e *.html} 
                 }
             }

       stage('Upload to AWS') {
             steps {
                 withAWS(region:'us-west-2',credentials:'aws-static') {
                 sh 'echo "Uploading content with AWS creds"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'pacho-udacity-jenking-pipeline-demo')
                 }
             }
        }
    }
}
