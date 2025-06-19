pipeline {
    agent any

    environment {
        BUILD_DIR = 'build'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/quanzzzzzz/MMM.git'
            }
        }

        stage('Prepare Build') {
            steps {
                echo 'Copying static files to build directory...'
                bat 'mkdir %BUILD_DIR%'
                bat 'copy *.html %BUILD_DIR%'
                bat 'copy *.css %BUILD_DIR%'
                bat 'copy *.js %BUILD_DIR%'
                bat 'copy *.png %BUILD_DIR%'
                bat 'copy *.jpg %BUILD_DIR%'
            }
        }

        stage('Archive Build') {
            steps {
                archiveArtifacts artifacts: "${BUILD_DIR}/**", fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Web tĩnh đã được build thành công!'
        }
        failure {
            echo '❌ Có lỗi khi build web!'
        }
    }
}
