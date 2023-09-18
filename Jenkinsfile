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
                        git checkout jenkins-test
                        docker build -t $DOCKER_HUB_USERNAME/project-server:cloud4y .
                    '''
                }
            }
        }
        stage('Запуск') {
            steps {
                script {
                    sh "docker compose docker-compose.yml up"
                }
            }     
                
        }
    }
}
