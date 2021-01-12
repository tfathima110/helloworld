
pipeline {
    agent any
    stages {
        stage ("git clone") {
            steps {
                git url: 'https://github.com/jshankarraju/helloworld.git'
            }    
        }

        stage ("Build") {
            steps {
                script {
                   sh  "mvn clean install"
                }
            }
        }

        stage ("CD") {
            steps {
                script {
                    sh ""
                    //sh "ansible-playbook -i {{inventory_name}} playbook"
                }
            }
        }
        
        stage ("notify") {
            steps {
                emailext body: 'this is status of job "${BUILD_URL}"', subject: 'Job Status', to: 'jshankarraju@gmail.com'
            }
        }
    }
}
