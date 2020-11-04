pipeline{

    agent {
        label 'golang'
    }

    stages {
        stage('install keptn cli') {
            steps {
                script {
                    container('golang') {
                        sh "curl -sL https://get.keptn.sh | bash"
                        withCredentials([usernamePassword(credentialsId: 'keptn-auth', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                            sh "keptn auth --endpoint=${USER} --api-token=${PASS}"
                        }
                        sh "keptn status"
                    }
                }
            }
        }
    }
    
}