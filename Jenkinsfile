pipeline {
    agent any

    environment {
        SONAR_IP = "54.226.50.200"
        SONAR_TOKEN = "sqp_64ee5dab880dd696661d5ff78f39348288cfb26d"
    }
    stages {
        stage('Restore') {
            steps {

                sh "dotnet restore"

            }
        }
  
        stage('Bulid') {
            steps {

                sh "dotnet build"
            }
        }
    

        stage('Test') {
            steps {

                sh "dotnet test"
            }
        }

        stage('Quality Scan') {
            steps {
                sh '"dotnet-sonarscanner begin /k:"dareen-dotnet-sample-proj" /d:sonar.host.url="http://$SONAR_IP"  /d:sonar.login="$SONAR_TOKEN""'
                sh 'dotnet build'
                sh 'dotnet-sonarscanner end /d:sonar.login="$SONAR_TOKEN"'
            }
        }
    
        stage('Publish') {
            steps {

                sh "dotnet publish"
            }


            post {
                success {
                    archiveArtifacts artifacts: '*/bin/Debug/net6.0/**.dll', followSymlinks: false
                }
            }
        }
    
    }
}
