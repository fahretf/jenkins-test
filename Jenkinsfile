pipeline {
   agent any

   stages {
     

      stage('Build Docker Image') {
         steps {
            echo 'Building Docker Image...'
            sh 'docker build -t nodejs-app .'
         }
      }

      stage('Deploy') {
         steps {
            echo 'Deploying Container...'
            sh '''

               if [ "$(docker ps -q --filter name=nodejs-app)" ]; then
                   docker stop nodejs-app
                   docker rm nodejs-app
               fi
               
               
              docker run --name nodejs -p 3000:3000 -d nodejs-app
            '''
         }
      }
   }
}

