pipeline{
    agent {
  label 'aws-agent'
}

    stages{
        stage('build'){
            steps{
                script{
                    sh 'mvn clean package'
                }
            }
        }
        stage('test'){
            steps{
                script{
                    echo "test is progress"
                }
            }
        }
    }

post {
  success {
    slackSend channel: '#jenkins-ci', message: "Build Success - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", teamDomain: 'jenkins-kjc6798', tokenCredentialId: 'slack-notification'
  }
  failure {
    slackSend channel: '#jenkins-ci', message: "Build Failure - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", teamDomain: 'jenkins-kjc6798', tokenCredentialId: 'slack-notification'
  }
}


}