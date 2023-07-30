pipeline {
  agent any
  stages {
    stage('Install dependencies') {
      steps {
        sh 'npm ci'
      }
    }

    stage('Check Style') {
      steps {
        sh 'npm run lint'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test'
      }
    }

    stage('Release') {
      steps {
        sh '''
          oc project bsck-greetings
          oc start-build greetings-console --follow --wait
          '''
      }
    }

  }
}