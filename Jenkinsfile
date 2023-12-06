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
          withDockerRegistry([credentialsId: '897c9bb0-8fee-4c2d-8db3-ebbfe78695dc', url: 'https://registry.hub.docker.com']) {
            docker.withRegistry('', 'DOCKER_HUB_CREDENTIALS') {
              // Your Docker-related steps here
              sh "echo \$SeCure@321#\\$ | docker login -u \$saaru789 --password-stdin"
              
              // Tag the Docker image before pushing
              docker.image('my-node-app:latest').push()
            }
          }
        }
      }
    }

    stage('Run') {
      steps {
        script {
          // Run the Docker container
          docker.image('my-node-app:latest').withRun('-p 3000:3000 -d')
        }
      }
    }
  }
}

