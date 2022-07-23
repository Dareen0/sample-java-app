pipeline {
    agent any
    stages {
        stage('Restore') {
            steps {

                sh 'dotnet restore'

            }
        }
  
        stage('Build') {
            steps {

                sh 'dotnet build'
            }
        }
    

        stage('Test') {
            steps {

                sh 'dotnet test'
            }
        }
    
        stage('Publish') {
            steps {

                sh 'dotnet publish'
            }


            post {
                success {
                    archiveArtifacts artifacts: '*/bin/Debug/net6.0/**.dll', followSymlinks: false
                }
            }
        }
    
    }
}
