node('linux'){
    
    stages {
        stage('Unit Tests') {
            git 'https://github.com/Jatt-mohnson/java-project.git'
            sh 'ant -f test.xml -v'
            
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
