pipeline {
    agent any
    
    environment {
        DOCKER_HUB_USERNAME = credentials('DOCKER_HUB_USERNAME')
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh '''
                        docker ps
                        whoami
                        groups
                        ls -l /usr/local/bin/docker-compose
                    '''
                }
            }
        }
    }

}
