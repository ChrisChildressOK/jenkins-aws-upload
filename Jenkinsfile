pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }      
         stage('Upload to AWS') {
              steps {
                  withAWS(endpointUrl:'https://742ab4690478f7406e67b636b9fdfdf6.r2.cloudflarestorage.com ',credentials:'CF-R2-Keys') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, file:'app.py', bucket:'builds', path:"/")
                  }
              }
         }
     }
}
