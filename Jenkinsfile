pipeline {
    agent any
    stages {
        stage('Validate') {
            steps {

                sh "mvn validate"
                sh "mvn clean"
            }
        }
    }
    stages {
        stage('Bulid') {
            steps {
                
                sh "mvn compile"
            }
        }
    }
    stages {
        stage('Test') {
            steps {
                sh "mvn test"
            }
            post{
            always{
                junit '**/target/surefire-reports/Test-*.xml'
             }
            }
        }
    }
    stages {
        stage('Package') {
            steps {
                sh "mvn package"
            }
            post{
                success{
                    archiveArtifacts artifacts: '**/target/**.war', followSymlinks: false
                }
            }
        }
    }
}
