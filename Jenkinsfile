pipeline {
  agent any
  stages {
    stage('GetIP') {
      parallel {
        stage('GetIP') {
          steps {
            bat 'ipconfig'
          }
        }

        stage('Date') {
          steps {
            powershell 'Get-Date'
          }
        }

      }
    }

    stage('CheckIfUnix') {
      steps {
        isUnix()
      }
    }

    stage('PrintMSG') {
      steps {
        input 'OK?'
      }
    }

  }
}