pipeline {
    agent any

    stages {
        stage('Unit Tests') {
            steps {
                ant -f 'test.xml' -v
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
