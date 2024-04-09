pipeline {
    agent any
    tools {
        maven 'Maven' 
    }
    stages {
        stage("Test") {
            steps {
                // mvn test
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
                // Deploy to Apache HTTP Server
                sh "scp -i ~/.ssh/id_rsa /var/lib/jenkins/workspace/Test-jenkins-war/target/*.war user@13.235.45.71:/var/www/html/app/"
            }
        }
        stage("Deploy on Prod") {
            input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            steps {
                // Deploy to Apache HTTP Server
                sh "scp -i ~/.ssh/id_rsa /var/lib/jenkins/workspace/Test-jenkins-war/target/*.war user@13.235.45.71:/var/www/html/app/"
            }
        }
    }
}
