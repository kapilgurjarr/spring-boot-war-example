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
                sh  """
                SOURCE_FILE=/var/lib/jenkins/workspace/Test-jenkins-war/target/*.war
                DEST_FOLDER=/var/www/html/
                sudo cp -a \$SOURCE_FILE \$DEST_FOLDER
                """
            }
        }
        stage("Deploy on Prod") {
            input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            steps {
                // Deploy to Apache HTTP Server
                sh """ 
                SOURCE_FILE=/var/lib/jenkins/workspace/Test-jenkins-war/target/*.war
                DEST_FOLDER=/var/www/html/
                sudo cp -a \$SOURCE_FILE \$DEST_FOLDER
                """
            }
        }
    }
}
