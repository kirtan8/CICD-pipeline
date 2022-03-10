pipeline{
    agent any 
    environment{
        VERSION = "${env.BUILD_ID}"
    }
    stages{
        stage("sonar quality check"){
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sq1') {
                            sh 'chmod +x gradlew'
                            sh './gradlew sonarqube'
                        }
                    }
                }  
            }
        }
    }
