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
            sh '''# Update package list
echo "6x@C2mSBnh57udz*" | sudo -S apt update

# Install Node.js (latest LTS version)
echo "6x@C2mSBnh57udz*" | sudo -S curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
echo "6x@C2mSBnh57udz*" | sudo -S apt-get install -y nodejs

# Upgrade npm to the latest version
echo "6x@C2mSBnh57udz*" | sudo -S npm install -g npm@latest

# Create a new React app
npx create-react-app my-app

# Install react-router-dom for routing
cd my-app
npm install react-router-dom
'''
          }
        }

      }
    }

  }
}