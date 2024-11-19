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
        }
      }
    }
    stage('Run tests'){
      steps{
        script{
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