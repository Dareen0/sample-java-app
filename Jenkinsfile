pipeline {
    agent any

    environment{
        DEMO= "1.1"
    }
    stages {
        stage('Fetch Code') {
            steps {
                echo 'Fetch Code'
                sh 'echo "Hi I am running first shell"'
            }

        }
        
         stage('Build') {
            steps {
                echo 'Build'
            }
        }
        
         stage('Test') {
            steps {
                echo 'Test'
            }
        }
        
         stage('Deploy') {
            steps {
                echo 'Deploy'
            }
        }
    }
}
