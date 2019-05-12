	
node('linux') {   
	stage('Unit Test') {    
		git 'https://github.com/jatt-mohnson/java-project.git'
		sh 'ant -f test.xml -v'   
		junit 'reports/result.xml'
	}   
	stage('Build') {    
		sh 'ant -f build.xml -v'   
		sh 'aws cloudformation create-stack --region us-west-1 --stack-name myteststack --template-url https://s3.amazonaws.com/ust-john3179/jenkins-cf.json --parameters ParameterKey=JenkinsPassword,ParameterValue=test1 ParameterKey=JenkinsSlaveNum,ParameterValue=1'
	}   
	stage('Deploy') {    
		sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://ust-john3179/'
	}
	stage('Report') {
		withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'AWS_Test', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
			sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
		}
	}	
}



