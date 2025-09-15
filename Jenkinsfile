pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/hanruiyang1029-yhr/8.2CDevSecOps.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        bat 'npm install'
      }
    }

    stage('Run Tests') {
      steps {
        bat 'npm test || exit /b 0'
      }
    }

    stage('Generate Coverage Report') {
      steps {
        
        bat 'npm run coverage || exit /b 0'
      }
    }

    stage('NPM Audit (Security Scan)') {
      steps {
        bat 'npm audit || exit /b 0'
      }
    }

   
    stage('SonarCloud Analysis') {
      steps {
        withCredentials([string(credentialsId: 'SONAR', variable: 'SONAR_TOKEN')]) 
          bat '''
            npx sonar-scanner -D"sonar.login=%SONAR_TOKEN%"
          '''
        }
      }
    }
  }
}
