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
                        docker build -t $DOCKER_HUB_USERNAME/project-server:cloud4y .
                    '''
                }
            }
        }

        stage('nichego') {
            steps {
                script {
                    sh '''
                        docker-compose up
                    '''
                }
            }
        }
    }

}
