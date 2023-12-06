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
          docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
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

