pipeline {
  agent any
  options { timestamps() }

  stages {
    stage('Build') {
      steps {
        echo 'Task: Compile/package the application.'
        echo 'Tool: Maven / Gradle / npm.'
      }
    }
    stage('Unit & Integration Tests') {
      steps {
        echo 'Task: Run unit tests and integration tests.'
        echo 'Tool: JUnit / Mocha / Jest / pytest.'
      }
    }
    stage('Code Analysis') {
      steps {
        echo 'Task: Static code quality analysis with quality gate.'
        echo 'Tool: SonarQube / SonarCloud / ESLint / Pylint.'
      }
    }
    stage('Security Scan') {
      steps {
        echo 'Task: Scan dependencies/source for vulnerabilities.'
        echo 'Tool: Snyk / OWASP Dependency-Check / npm audit.'
      }
    }
    stage('Deploy to Staging') {
      steps {
        echo 'Task: Deploy artifact to a Staging environment.'
        echo 'Tool: Docker + AWS CLI / Ansible.'
      }
    }
    stage('Integration Tests on Staging') {
      steps {
        echo 'Task: E2E/API tests against Staging.'
        echo 'Tool: Postman (Newman) / Cypress / Selenium.'
      }
    }
    stage('Deploy to Production') {
      steps {
        echo 'Task: Promote and deploy to Production with rollback strategy.'
        echo 'Tool: Ansible / AWS CLI / Kubernetes (kubectl/Helm).'
      }
    }
    stage('Notification') {
      steps {
        echo 'Task: Send deployment notification to the team.'
        echo 'Tool: Email / Slack / Teams.'
      }
    }
  }
}
