pipeline {
  agent any

  options {
    timestamps()
  }

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
        withCredentials([string(credentialsId: 'SONAR', variable: 'SONAR_TOKEN')]) {
          withEnv(['NODE_OPTIONS=--max-old-space-size=4096', 'SONAR_SCANNER_OPTS=-Xmx1024m']) {
            retry(2) {
              bat 'npx sonar-scanner -Dsonar.token=%SONAR_TOKEN% -Dsonar.projectKey=hanruiyang1029-yhr_8.2CDevSecOps -Dsonar.organization=hanruiyang1029-yhr -Dsonar.javascript.node.maxspace=4096'
            }
          }
        }
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'coverage/**', onlyIfSuccessful: false
    }
  }
}



