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
                bat 'docker login -u srilekha0208 -p dckr_pat_c-MalHZJ8c0kFDCHIKHNEkPlEFk'
            }
        }

        stage('Test') {
    steps {
        echo 'Testing the application'
        bat 'docker rm -f test_container || exit 0'
        bat 'docker run -d -p 5000:5000 --name test_container my-python-application'
    }
}

        stage('Deploy') {
            steps {
                echo 'Deploying the application'
                bat 'docker tag my-python-application srilekha0208/my-python-application:latest'
                bat 'docker push srilekha0208/my-python-application:latest'
            }
        }
    }

    post {
        success {
            echo 'Build successful'
        }
        failure {
            echo 'Build failed'
        }
    }
}
