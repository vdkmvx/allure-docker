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
                    sh "docker run -d olsoncarsen/project-server:cloud4y"
                }
            }     
                
        }
    }


    post {
        always {
            // Очищаем после себя контейнеры и образы
            script {
                def containerId = sh(script: 'docker ps -q --filter "name=olsoncarsen/project-server"', returnStdout: true).trim()
                sh 'docker stop ${containerId}'
                sh 'docker rm ${containerId}'
                sh 'docker rmi olsoncarsen/project-server:cloud4y'
            }
        }
    }
}
