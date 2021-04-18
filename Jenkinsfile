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
        
        docker.withRegistry('https://public.ecr.aws/s1u4y5t4/', 'git') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
