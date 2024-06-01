#!/usr/bin/env groovy

def gv

pipeline {
    agent any
    tools {
        maven 'maven'
    }

      environment {
         CRED = credentials('eslam1')
      }

   parameters {

       choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }


    stages {

        stage('init') {
            steps {
                script {
                    gv = load "script.groovy"
                   echo "Username: $CRED_USR"

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
            input{
                message "select the environment to deploy to"
                ok "Done"
                parameters {   
                    choice(name: 'ENV', choices: ['dev', 'staging', 'prod'], description: '')
                }
            }          
            steps {
                script {
                    gv.DeployApp()
                    sh 'docker build -t eslam1/jenkins-repo:3.0 .'
                    echo "deployine to ${ENV}"

                    withCredentials([usernamePassword(credentialsId: 'eslam1', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh "echo $PASS | docker login -u $USER --pasword-stdin"
                    sh 'docker push eslam1/jenkins-repo:3.0'
                    }
                }
            }
        }
    }
}
