 pipeline
 {
    agent
    {
      label 'NODEJS'
     }
    stages {
       stage('Download dependencies')
       {
         steps {
            sh '''
               npm install
            '''
         }
        }

       stage('prepare artifact')
       {
            steps
           {
              sh '''

                 zip -r user.zip node_modules server.js

              '''
           }
       }
           stage('upload artifacts to nexus')
           {
              steps
              {
                 sh '''
                    curl -f -v -u admin:admin --upload-file user.zip http://172.31.20.130:8081/repository/user/user.zip
                 '''
              }
           }


    }
 }