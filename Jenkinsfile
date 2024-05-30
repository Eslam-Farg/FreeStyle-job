#!/usr/bin/env groovy

pipeline {
    agent any

        environment {
        BRANCH = "${env.BRANCH_NAME}"
    }

    
    stages {
        stage('Conditional Stage') {
            when {
                expression {
                    BRANCH != 'main'
                }
            }
            steps {
                echo $BRANCH
                echo "This stage runs only for the 'main' or 'develop' branch."
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
