pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application'
                bat 'docker build -t my-python-application .'
            }
        }
        
        stage('User Login') {
            steps {
                echo 'Logging into Docker Hub'
                bat 'docker login -u <username> -p <password>'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing the application'
                
                bat 'docker run -d -p 5000:5000 --name test_container my-python-application'
                

            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying the application'
                bat 'docker push <username>/my-python-application:latest'
            }
        }
    }
    
     post{
        success{
            echo 'Build successful'

        }
        failure{
            echo 'Build failed'
        }
     }