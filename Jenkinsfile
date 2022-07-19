pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')

        AWS_S3_BUCKET = "artefact-bucket-app"
        ARTEFACT_NAME = "hello-world.war"
    }
    stages {
        stage('Validate') {
            steps {

                sh "mvn validate"

                sh "mvn clean"
            }
        }
    
  
        stage('Bulid') {
            steps {

                sh "mvn compile"
            }
        }
    

        stage('Test') {
            steps {

                sh "mvn test"
            }

            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
    
    
        stage('Package') {
            steps {

                sh "mvn package"
            }


            post {
                success {
                    archiveArtifacts artifacts: '**/target/**.war', followSymlinks: false
                }
            }
        }
        stage('Publish artefacts to s3 bucket') {
            steps {

                sh "aws configure set region us-east-1"

                sh "aws s3 cp ./target/**.war s3://$AWS_S3_BUCKET/$ARTEFACT_NAME"
            }
        }
        stage('Deploy') {
            steps {

            sh "Last Stage"
            
            }
        }
    }
}
