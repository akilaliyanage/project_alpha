pipeline {

    agent none
    
    stages {
        
        stage('Cleanup Workspace') {
            
            agent{
                label "master"
            }
            
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace"
                """
            }
        }

        stage('Code Checkout') {
            
            agent{
                label "master"
            }
            
            steps {
                echo "Pulling the code form the GitHub"
                git credentialsId: '2dea0e99-99af-4c30-9650-f4a0a1dc7570', url: 'https://github.com/akilaliyanage/project_alpha.git'
            }
        }

        stage('Code Build') {
            
            agent{
                label "master"
            }
            
            
            steps {
                 echo "Installing NPM dependencies"
                 sh 'npm install --silent'

                 echo "Building the docker image"
                 sh 'docker build -t project_aplha:latest .'
            }
        }

        stage('Running the application') {
            
            agent{
                label "master"
            }
            
            
            steps {
                echo "NPM start"
                sh 'npm start --silent'
            }
        }

    }   
}
