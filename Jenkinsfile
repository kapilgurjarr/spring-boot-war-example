pipeline {
    agent any
    tools {
        maven 'Maven' 
    }
    stages {
        stage("Test") {
            steps {
                sh "mvn test"
            }
        }
        stage("Build") {
            steps {
                sh "mvn package"
            }
        }
        stage("Deploy on Test") {
            steps {
                script {
                    def sourceFile = "/var/lib/jenkins/workspace/Test-jenkins-war/target/*.war"
                    def destFolder = "/var/www/html/"
                    sh "cp -a ${sourceFile} ${destFolder}"
                }
            }
        }
        stage("Deploy on Prod") {
            input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            steps {
                script {
                    def sourceFile = "/var/lib/jenkins/workspace/Test-jenkins-war/target/*.war"
                    def destFolder = "/var/www/html/"
                    sh "cp -a ${sourceFile} ${destFolder}"
                }
            }
        }
    }
}
