node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       app = docker.build("brandonjones085/test")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
      steps {
        script {
          docker.withRegistry('https://625940664891.dkr.ecr.us-east-1.amazonaws.com/',
           'ecr:us-east-1:my.aws.cred') {
            def myImage = docker.build('test')
            myImage.push('latest')
          }
          }
        }
    }
}
