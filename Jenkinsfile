#!/usr/bin/env groovy

pipeline {
    agent any
    stages {
        stage('init') {
           when {
               expression{
               BRANCH_NAME != 'main'
           }
           }
            steps {
                script {
                    
                    echo "Hello! this is Main branch..."
                }
            }
        }
        stage('build') {
            steps {
                script {
                    echo "Building the application..."
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
                }
            }
        }
    }
}
