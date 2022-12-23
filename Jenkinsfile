pipeline {
    agent any
triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('trigger') {
            steps {
                git branch: 'main', url: 'https://github.com/rajnikanth1999/saleor.git'
            }
        }
        stage('build') {
            steps {
                sh 'docker image build -t praveenrajnikanth/workshop:saleor .'
            }
        }
        stage('push') {
            steps {
                sh 'docker image push praveenrajnikanth/workshop:saleor'
            }
        }
        stage('container') {
            steps {
                sh 'docker container run -d -P praveenrajnikanth/workshop:saleor'
            }
        }
        stage('terraform') {
            steps {
                build job: 'terraform'
            }
        }
    }
}