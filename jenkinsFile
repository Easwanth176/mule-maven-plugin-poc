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
                CLIENT_ID = credentials('anypoint_credentials')
                CLIENT_SECRET = credentials('anypoint_credentials')
            }
            steps {
                bat """ mvn clean deploy -DmuleDeploy -Dclient_id=${CLIENT_ID} -Dclient_secret=${CLIENT_SECRET}"""
            }
        }
    }
}

