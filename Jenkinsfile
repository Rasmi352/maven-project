pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to Staging'){
            steps {
                 build job:'Deploy-to-Staging'
                 success{
                      echo 'Deployment to staging environment is successful..Hurray!!'
                 }
            }
        }

    }
}