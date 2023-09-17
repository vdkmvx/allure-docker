pipeline {
    agent any

    
    environment {
        TELEGRAM_BOT_TOKEN = credentials('TELEGRAM_BOT_TOKEN')
    }

    stages {
        stage('Build') {
            steps {
		echo " ============== docker login =================="
                script {
                    sh '''
                        curl -X GET "https://api.telegram.org/bot${TELEGRAM_BOT_TOKEN}/sendMessage?chat_id=1641151245&text=Собираю+новую+версию+Server+Пространства"
                    '''
                }
            }
        }
    }
}