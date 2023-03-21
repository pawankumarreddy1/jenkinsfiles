pipeline {
    agent any

    stages {
        stage('ci') {
            steps {
                sh 'zip -r index.html.zip . -i *'
                sh 'aws s3 mb s3://anand-pavan-2'
                sh 'aws s3 cp index.html.zip s3://anand-pavan-2 '
                
            }
        }
        stage('cd') {
            steps {
                sh 'aws s3 cp s3://anand-pavan-2/index.html.zip . '
                sh 'unzip index.html.zip '
                sh 'ssh root@172.31.52.141 '
                sh 'scp index.html root@172.31.52.141:/var/www/html/
                
            }
        }
    }
}
