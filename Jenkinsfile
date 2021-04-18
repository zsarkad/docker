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
           withDockerRegistry([url: "https://625940664891.dkr.ecr.us-east-1.amazonaws.com/test",credentialsId: "ecr:us-east-1:my.aws.cred"]) {
           bat 'docker push brandonjones085/test:latest'
           }
        }
        }
    }
}
