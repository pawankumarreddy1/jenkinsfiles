pipeline {
    agent any

    stages {
        stage('ci') {
            steps {
                sh 'zip -r html-helloworld-$BUILD_NUMBER.zip *'
                sh 'aws s3 cp html-helloworld-$BUILD_NUMBER.zip s3://pavanm123/'
            }
        }
         stage('cd') {
            steps {
                sh 'rm -fr *'
                sh 'aws s3 cp s3://pavanm123/html-helloworld-$BUILD_NUMBER.zip .'
                sh 'unzip html-helloworld-$BUILD_NUMBER.zip'
                sh 'scp index.html root@10.0.0.177:/var/www/html/'
            }
        }
    }
}
