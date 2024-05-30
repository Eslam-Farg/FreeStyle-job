#!/usr/bin/env groovy

pipeline {
    agent any
    tools {
        maven 'maven'
    }

    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }


    stages {

        stage('Test') {
            when {
                expression {
                    param.executeTests == true
                }
            }
            steps {
                script {
                    echo "Testing app............................................"
                    
                }
            }
        }

        stage('build') {
            steps {
                script {
                    echo "Building the application..."
                    sh 'mvn package'
                }
            }
        }
        stage('test') {
            steps {
                script {
                    echo "Testing the application..."
                    
                }
            }
        }
        stage('deploy') {
            steps {
                script {
                    echo "Deploying the application..."
                    sh 'docker build .'
                }
            }
        }
    }
}
