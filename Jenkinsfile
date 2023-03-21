pipeline {
    agent any

    stages {
        stage('ci') {
            steps {
                sh 'zip -r index.html-$BUILD_NUMBER.zip . -i *'
                sh 'aws s3 mb s3://anand-pavan-2'
                sh 'aws s3 cp index.html-$BUILD_NUMBER.zip s3://anand-pavan-2 '
                
            }
        }
        stage('cd') {
            steps {
                sh 'rm -fr * '
                sh 'aws s3 cp s3://anand-pavan-2/index.html-$BUILD_NUMBER.zip . '
                sh 'unzip index.html-$BUILD_NUMBER.zip '
                sh 'scp index.html root@172.31.52.141:"/var/www/html/" '
                
            }
        }
    }
}
