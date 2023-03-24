pipeline {
    agent any

    stages {
        stage('ci') {
            steps {
                sh 'zip -r index.html-$BUILD_NUMBER.zip . -i *'
                sh 'aws s3 mb s3://abdul-pavan'
                sh 'aws s3 cp index.html-$BUILD_NUMBER.zip s3://abdul-pavan '
                
            }
        }
        stage('cd') {
            steps {
                sh 'rm -fr * '
                sh 'aws s3 cp s3://abdul-pavan/index.html-$BUILD_NUMBER.zip . '
                sh 'unzip index.html-$BUILD_NUMBER.zip '
                sh 'scp index.html root@172.31.51.220:"/var/www/html/" '
                
            }
        }
    }
}
