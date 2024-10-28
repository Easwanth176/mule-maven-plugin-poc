pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                bat 'mvn clean install'
            }
        }
        
        stage('Deploy CloudHub') {
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypoint_credentials')
            }
            steps {
                bat """ mvn clean deploy -DmuleDeploy -Dclient_id=${ANYPOINT_CREDENTIALS_USR} -Dclient_secret=${ANYPOINT_CREDENTIALS_PSW} -X -e"""
            }
        }
    }
}

