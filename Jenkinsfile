properties([pipelineTriggers([githubPush()])])

node('linux') { 
    stage('Test') {
        sh 'ant -f test.xml -v
    }
    stage('Build') { 
        sh 'ant'
    }
    stage('Deploy') {
        
    }
    stage('Report') {
        junit 'reports/*.xml' 
    }
}
