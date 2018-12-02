properties([pipelineTriggers([githubPush()])])

node('linux') { 
    stage('Test') {
        sh 'ant -f test.xml   
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
