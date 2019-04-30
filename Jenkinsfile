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
            steps {

                sh "$(which aws) s3 cp dist/rectangle-${BUILD_NUMBER}.jar s3://ust-john3179"
            }
                    }
        stage('Report') {
            steps {
                echo 'Reporting'
            }
        }
    }
}
