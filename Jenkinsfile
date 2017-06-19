pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/fab30/pipelinedemo.git', branch: 'master', credentialsId: 'github-fab30', changelog: true)
      }
    }
    stage('Build') {
      steps {
        tool 'M3'
        sh '/tmp/apache-maven-3.5.0/bin/mvn build'
      }
    }
    stage('Unitary test') {
      steps {
        parallel(
          "Unitary test": {
            sleep 10
            
          },
          "Fonctionnal test": {
            sleep 15
            
          },
          "Integration test": {
            sleep 5
            
          }
        )
      }
    }
    stage('MEP ?') {
      steps {
        input(message: 'Do you want push in production ?', id: 'mep')
      }
    }
    stage('MEP') {
      steps {
        sleep 5
        echo 'Product in production !'
      }
    }
  }
}