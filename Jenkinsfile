pipeline{
  agent any

  stages{
    stage('Checkout'){
      steps{
        checkout scm
      }
    }

    stage('Install dependencies'){
      steps{
        script{
          git branch: 'main', url: 'https://github.com/CrimsonKingCodes/StudentRegistryAppDemo'
        }
      }
    }
    stage('Start application and run tests'){
      steps{
        script{
          bat 'start /b npm start'
          bat 'wait-on http://localhost:8080'
          bat 'npm test'
        }
      }
    }
  }

  post{
    always{
      echo 'CI pipeline completed'
    }
  }
}