pipeline {
    agent {
        label '!windows'
    }

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }

    stages {
        stage('Build') {
            steps {
                echo "Database engine is ${DB_ENGINE}"
                echo "DISABLE_AUTH is ${DISABLE_AUTH}"
                sh 'printenv'
            }
        }
    }
    
    post {
        always {
            echo 'One way or another, I have finished'
        }
        success {
            mail to: 'kartheek.c@zoho.com',
                 subject: "Sucess Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Things are fine with ${env.BUILD_URL}"
        }
    }
}
