#!/usr/bin/env groovy

pipeline {
    agent any
    tools {
        maven 'maven'
    }


    stages {

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
                    sh 'mvn Test'
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
