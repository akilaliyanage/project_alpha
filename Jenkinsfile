pipeline {

    agent none
    
    node master
    
    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                echo "Pulling the code form the GitHub"
                git credentialsId: '2dea0e99-99af-4c30-9650-f4a0a1dc7570', url: 'https://github.com/akilaliyanage/project_alpha.git'
            }
        }

        stage('Code Build') {
            steps {
                 echo "Installing NPM dependencies"
                 sh 'npm install --silent'

                 echo "Building the docker image"
                 sh 'docker build -t project_aplha:latest'
            }
        }

        stage('Running the application') {
            steps {
                echo "NPM start"
                sh 'npm start --silent'
            }
        }

    }   
}
