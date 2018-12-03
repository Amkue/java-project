properties([pipelineTriggers([githubPush()])])

node('linux') { 
    stage('Test') {
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
    }
        stage('Build') { 
        sh 'ant -f build.xml -v'
    }
    stage('Deploy') {
        sh 'aws s3 cp /workspace/Assignment10/dist/rectangle-${BUILD_NUMBER}.jar s3://seis665.assignment10/'
    }
    stage('Report') {
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'eab26c6b-d1af-4747-9bf0-9d1af6814139', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
            sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins' 
        }
    }
}
