pipeline {
    agent any
    tools{
        maven 'Maven3'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Java-Techie-jt/devops-automation']]])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t java-itheroes .'
                }
            }
        }
        stage('App deploy on Docker comtainer'){
            steps{
                script{
                   sh 'docker run -itd --name itheroes java-itheroes /bin/bash'
                }

            }
        }
    }
}
