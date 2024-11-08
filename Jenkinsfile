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

        stage('Front-End Dependencies Installation') {
          steps {
            sh '''sudo apt update
sudo npm install npm@latest
sudo apt-get install nodejs
npx create-react-app my-app
npm install react-router-dom
'''
          }
        }

      }
    }

  }
}