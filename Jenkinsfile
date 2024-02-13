pipeline{
    agent{ label 'JDK11'}
    options{ 
        (time: 1, unit: 'HOURS'),
        retry(2)
         }
    triggers {
        cron('0 * * * *') 
        }
    stages{
        stage('Source code'){
            steps {
                git( url: 'https://github.com/lokeshrajchukka/spring-petclinic.git',
                branch: 'main')
            }
        }
        stage('Buld the code'){
            steps {
                sh script: 'mvn clean package'
            }
        }
        stage('reporting'){
            steps {
                junit testResults: 'target/surefire-reports/*.xml'
            }
        }
    }
    post {
        success {
            //send success mail
            echo "Successs"
        }
        failure {
            //send unsuccessfull mail
            echo "Failure"
        }
    }

}