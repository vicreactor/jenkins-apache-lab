pipeline {
    agent any

    stages {
        stage('install Apache2') {
            steps {
                sh '''whoami
                sudo -n whoami
                sudo apt update
                sudo apt install -y apache2
                sudo service apache2 start
                '''
            }
        }
        stage('generate apache.log') {
            steps {
                sh '''
                curl http://localhost
                curl http://localhost/something-not-exist
                '''
            }
        }
        stage('Check logs') {
            steps {
                sh '''
                grep " 4[0-9][0-9] " /var/log/apache2/access.log || echo "No 4xx logs"
                grep " 5[0-9][0-9] " /var/log/apache2/access.log || echo "No 5xx logs"
                '''
            }
        }
    }
}
