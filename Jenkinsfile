pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World!!'
            }
        }
        stage('Build') {
            steps {
                echo 'Builidng'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
                withCredentials([[
                                $class: 'AmazonWebServicesCredentialsBinding',
                                credentialsId: 'MyAWS',
                                accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                                secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                                    sh(script: 'aws s3 cp /var/lib/jenkins/workspace/JenkinsPipline/index.html s3://test-env-jenkins-hukum')
                            }
            }
        }
        stage('Test') {
            steps {
                echo 'Testiong'
            }
        }
        stage('Release') {
            steps {
                echo 'Releaseing'
            }
        }
    }
}
