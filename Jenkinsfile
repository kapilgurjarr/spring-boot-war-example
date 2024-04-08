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
                sh "scp -i /path/to/ssh/key target/*.war user@13.233.123.102:/var/www/html/app.war"
            }
        }
        stage("Deploy on Prod") {
            input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            steps {
                // Deploy to Apache HTTP Server
                sh "scp -i /path/to/ssh/key target/*.war user@13.233.123.102:/var/www/html/app.war"
            }
        }
    }
}
