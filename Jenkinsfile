pipeline{

    // agent {
    //     label 'python'
    // }
    agent any

    stages {
        stage('install keptn cli') {
            steps {
                script {
                    sh "curl -OL https://github.com/keptn/keptn/releases/download/0.7.2/0.7.2_keptn-linux.tar"
                    sh "tar -xvf 0.7.2_keptn-linux.tar"
                    sh "ls -la"
                    sh "chmod +x keptn"
                    withCredentials([usernamePassword(credentialsId: 'keptn-auth', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                        sh "./keptn auth --endpoint=${USER} --api-token=${PASS}"
                    }
                    sh "./keptn status"
                }
            }
        }
        stage('deploy') {
            when {
                expression {
                    env.GIT_BRANCH == "master"
                }
            }
            steps {
                script {
                    sh "keptn send event new-artifact --project=sockshop --service=carts --image=docker.io/keptnexamples/carts --tag=0.11.1"
                }
            }
        }
    }
    
}