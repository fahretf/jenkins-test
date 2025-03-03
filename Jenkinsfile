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

               if [ "$(docker ps -q --filter name=nodejs)" ]; then
                   docker stop nodejs
                   docker rm nodejs
               fi
               
               
              docker run --name nodejs -p 3000:3000 -d nodejs-app
            '''
         }
      }
   }
}

