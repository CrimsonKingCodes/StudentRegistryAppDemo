pipeline{
  agent any

  environment{
    NODE_VERSIONS = '18.x'
  }

  tools{
    nodejs "${NODE_VERSIONS}"
  }

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
          bat 'npm start &'
          bat 'wait-on http://localhost:8090'
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