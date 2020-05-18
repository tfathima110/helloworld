#!/usr/bin/env groovy

//def server = Artifactory.server 'myjfrog'

pipeline {
    agent any
    stages {
        stage('SCM Git clone') {
            steps {
               git credentialsId: 'github', url: 'https://github.com/tejesh555/helloworld.git'
            }       
        }

        stage('BUILD') {
            steps {
                script {
                    sh 'mvn clean install'
                }
            }
        }

        stage("test") {
            steps {
                script {
                    sh """
                           echo 'tejesh'
                           echo 'ram'
                           echo 'likitha'
                         """
                }
            }
        }

        stage ('publish') {
            steps {
                script {

                    rtUpload (
                        serverId: 'myjfrog',
                        spec: '''{
                              "files": [
                                {
                                  "pattern": "target/*.jar",
                                  "target": "helloworld/"
                                }
                             ]
                        } '''
                    )
                    
                }
            }
        }

        stage ('deploy') {
            steps{ 
                script {
                    sh 'echo "ansibleAhoc-command"'
                }
            }
        }
    }
    post {
        always {
            println "${env.BUILD_URL}"
        }
    }
}

