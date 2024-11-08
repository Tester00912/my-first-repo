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

        stage('Build-Config') {
          steps {
            sh '''#!/bin/bash

sudo apt-get update -y
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update -y

sudo apt-get install -y docker-ce docker-ce-cli containerd.io

sudo systemctl start docker
sudo systemctl enable docker'''
          }
        }

      }
    }

    stage('Front-End Unit Tests') {
      steps {
        sh '''#!/bin/bash

# Define the project name
PROJECT_NAME="my-react-app"

# Move to the workspace directory
cd "$WORKSPACE" || exit 1

# Check if the project directory already exists
if [ -d "$PROJECT_NAME" ]; then
  echo "React project \'$PROJECT_NAME\' already exists. Skipping creation."
else
  # Create a new React app
  npx create-react-app "$PROJECT_NAME"
  
  # Confirm success
  if [ $? -eq 0 ]; then
    echo "React project \'$PROJECT_NAME\' created successfully."
  else
    echo "Failed to create React project." >&2
    exit 1
  fi
fi
'''
      }
    }

    stage('Build') {
      steps {
        sh '''#!/bin/bash

# Define the name of the Dockerfile
DOCKERFILE_NAME="Dockerfile"

# Check if a Dockerfile already exists to avoid overwriting
if [ -f "$DOCKERFILE_NAME" ]; then
  echo "Dockerfile already exists. Exiting to avoid overwriting."
  exit 1
fi

# Create the Dockerfile
cat <<EOL > $DOCKERFILE_NAME
# Use the official Node.js image as the base
FROM node:18

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json (if available)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the application source code
COPY . .

# Run tests using Jest
CMD ["npm", "test"]
EOL

# Confirm the Dockerfile creation
if [ -f "$DOCKERFILE_NAME" ]; then
  echo "Dockerfile created successfully."
else
  echo "Failed to create Dockerfile." >&2
  exit 1
fi
'''
      }
    }

  }
}