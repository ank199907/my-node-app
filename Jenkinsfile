pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        script {
          // Use the Docker plugin to build the Docker image
          docker.build('my-node-app:latest')
        }
      }
    }

    stage('Deploy') {
      steps {
        script {
          // Use Docker Hub credentials to push the Docker image
          docker.withRegistry('https://registry.hub.docker.com', '897c9bb0-8fee-4c2d-8db3-ebbfe78695dc') {
            docker.image('my-node-app:latest').push()
          }
        }
      }
    }

    stage('Run') {
      steps {
        script {
          // Run the Docker container
          docker.image('my-node-app:latest').run('-p 3000:3000 -d')
        }
      }
    }
  }
}

