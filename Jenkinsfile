pipeline{

    agent {
        label 'golang'
    }

    stages {
        stage('install keptn cli') {
            steps {
                container('golang') {
                    sh "curl -sL https://get.keptn.sh | bash"
                }
            }
        }
    }
    
}