pipeline {
    agent any

    stages {
        stage('Checkout Source') {
            steps {
                checkout scm
            }
        }

        stage('Serve Static Web') {
            steps {
                bat '''
                    echo === Serving web at http://localhost:8080 ===
                    start python -m http.server 8080
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Web đang chạy tại http://localhost:8080'
        }
        failure {
            echo '❌ Lỗi khi chạy server (kiểm tra repo hoặc Python).'
        }
    }
}
