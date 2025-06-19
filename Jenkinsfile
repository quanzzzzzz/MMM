pipeline {
    agent any

    stages {
        stage('Checkout Source') {
            steps {
                // Lấy code từ GitHub về Jenkins
                git branch: 'main', url: 'https://github.com/quanzzzzzz/Web4.git'
            }
        }

        stage('Serve Static Web') {
            steps {
                // Dùng Python để chạy server tại thư mục hiện tại
                bat '''
                    echo === Đang chạy Web Tĩnh trên http://localhost:8080 ===
                    start python -m http.server 8080
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Web đã chạy tại http://localhost:8080/bai4.html (tự mở trình duyệt để xem).'
        }
        failure {
            echo '❌ Có lỗi khi khởi chạy server. Kiểm tra xem Python đã cài chưa.'
        }
    }
}
