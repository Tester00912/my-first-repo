pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      parallel {
        stage('Checkout Code') {
          steps {
            git(url: 'https://github.com/Tester00912/my-first-repo/', branch: 'main')
          }
        }

        stage('Log') {
          steps {
            sh 'ls -la'
          }
        }

      }
    }

  }
}