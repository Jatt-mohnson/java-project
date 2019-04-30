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
                echo 'Building..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
                    }
        stage('Report') {
            steps {
                echo 'Reporting'
            }
        }
    }
}
