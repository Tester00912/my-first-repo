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
            sh '''# Update the package list
sudo apt update

# Install Node.js (LTS version) using sudo without the -E flag
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo bash -

# Install Node.js and npm
sudo apt-get install -y nodejs npm

# Install npm globally
sudo npm install -g npm@latest

# Create a new React app
npx create-react-app my-app

# Install react-router-dom in the new React app
cd my-app
npm install react-router-dom
'''
          }
        }

      }
    }

  }
}