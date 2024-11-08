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
            sh '''#!/bin/bash

# Update system and install dependencies
echo "Updating system..."
sudo apt-get update -y
sudo apt-get upgrade -y

# Install Node.js and npm if not already installed
echo "Installing Node.js and npm..."
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Install project dependencies
echo "Installing dependencies..."
npm install

# Run tests (you can replace this with your test command)
echo "Running tests..."
npm test

# Build the application (if applicable)
echo "Building the application..."
npm run build

# Start the application (if applicable)
echo "Starting the application..."
npm start

echo "Script completed successfully!"
'''
          }
        }

      }
    }

    stage('Front-End Unit Tests') {
      steps {
        sh 'cd root/curriculum-app/'
      }
    }

  }
}