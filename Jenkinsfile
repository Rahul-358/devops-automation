pipeline {
    agent any   // machine --> localmachine ---> cloud EC2
    tools{
        maven 'Maven3'  // java build tools // Maven, Gradle and ent
    }
    stages{
        stage('git code checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Java-Techie-jt/devops-automation']]])
            }
        }
        stage('Build code'){
            steps{
                script{
                    sh 'sh 'mvn clean install''
                }
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t java-itheroes .'  // docker images
                }
            }
        }
        stage('App deploy on Docker comtainer'){
            steps{
                script{
                   sh 'docker stop itheroes'
                   sh 'docker rm itheroes'
                   sh 'docker run -itd --name itheroes -p 80:8080 java-itheroes /bin/bash' // docker ps ---> running container
                }

            }
        }
    }
}
