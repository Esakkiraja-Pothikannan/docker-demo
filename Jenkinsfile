pipeline {
  environment {
    imagename = 'esakkirajapothikannan/docker-jenkins'
    registryCredential = 'dockerhub'
    dokcerImage
  }
  
  agent any
  
  stages {
    stage('Cloning Git Repo') {
      steps {
        git([url: 'https://github.com/Esakkiraja-Pothikannan/docker-demo.git', branch: 'master'])
      }
    }
    
    stage('Building Image') {
      steps {
        script {
          dockerImage = docker.build imagename
        }
      }
    }
    
    stage('Deploy Image') {
      steps {
        script {
          docker.withRegistry('', registryCredential)
          dockerImage.push('$BUILD_NUMBER')
          dockerImage.push('latest')
        }
      }
    }
    
  }
}
