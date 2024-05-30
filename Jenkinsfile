#!/usr/bin/env groovy

def gv

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

        stage('init') {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }

        stage('Test') {
            when {
                expression {
                    params.executeTests == true
                }
            }
            steps {
                script {
                    gv.TestApp()
                    
                }
            }
        }

        stage('build') {
            steps {
                script {
                    gv.BuildApp()
                    sh 'mvn package'
                }
            }
        }

        stage('deploy') {
            steps {
                script {
                    gv.DeployApp()
                    sh 'docker build .'
                }
            }
        }
    }
}
