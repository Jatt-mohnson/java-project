pipeline{
    agent any
    
    stages {
        stage('Unit Tests') {
            steps{
            sh 'ant -f test.xml -v'
            junit 'reports/result.xml'
            }
        }
        stage('Build') {
            steps {
                sh 'ant -f build.xml -v'
            }
        }
        stage('Deploy') {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'AWS user for jenkins', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) 
            steps {
                sh "aws s3 cp dist/rectangle-${BUILD_NUMBER}.jar s3://ust-john3179"
            }
                    }
        stage('Report') {
            steps {
                echo 'Reporting'
            }
        }
    }
}
