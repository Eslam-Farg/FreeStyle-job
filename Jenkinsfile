#!/usr/bin/env groovy

pipeline {
    agent any
    stages {
        stage('init') {

            steps {
                script {
                    echo "${BRANCH_NAME}"
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
